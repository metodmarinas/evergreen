<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Checkout - AquaFlex Pro</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts - Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc; /* Light blue-gray background */
        }
        .btn-primary {
            background-color: #10b981; /* Emerald green */
            color: white;
            padding: 0.75rem 2rem;
            border-radius: 9999px; /* Fully rounded */
            font-weight: 600;
            transition: background-color 0.3s ease;
        }
        .btn-primary:hover {
            background-color: #059669; /* Darker emerald */
        }
        .payment-method-card {
            border: 2px solid #e2e8f0;
            border-radius: 0.75rem;
            padding: 1.5rem;
            cursor: pointer;
            transition: all 0.2s ease-in-out;
        }
        .payment-method-card.selected {
            border-color: #10b981; /* Emerald green */
            box-shadow: 0 4px 6px rgba(16, 185, 129, 0.2);
            background-color: #ecfdf5; /* Light emerald */
        }
        .payment-method-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .modal {
            display: none; /* Hidden by default */
            position: fixed; /* Stay in place */
            z-index: 1000; /* Sit on top */
            left: 0;
            top: 0;
            width: 100%; /* Full width */
            height: 100%; /* Full height */
            overflow: auto; /* Enable scroll if needed */
            background-color: rgba(0,0,0,0.6); /* Black w/ opacity */
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background-color: #fefefe;
            margin: auto;
            padding: 2.5rem;
            border-radius: 1rem;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            width: 90%;
            max-width: 500px;
            text-align: center;
            position: relative;
        }
        .close-button {
            color: #aaa;
            position: absolute;
            top: 1rem;
            right: 1.5rem;
            font-size: 2rem;
            font-weight: bold;
            cursor: pointer;
        }
        .close-button:hover,
        .close-button:focus {
            color: #333;
            text-decoration: none;
            cursor: pointer;
        }
    </style>
</head>
<body class="text-gray-800">

    <!-- Header for Checkout Page -->
    <header class="bg-white shadow-md py-4 px-6 md:px-12 flex justify-center items-center rounded-b-xl">
        <div class="text-3xl font-bold text-emerald-600">Evergreen Checkout</div>
    </header>

    <main class="container mx-auto px-6 py-12 md:py-16 max-w-4xl">
        <h1 class="text-4xl md:text-5xl font-extrabold text-center text-emerald-800 mb-10">Finalizá tu Compra</h1>

        <div class="bg-white p-8 md:p-10 rounded-xl shadow-lg border border-gray-200">
            <p class="text-red-600 font-semibold text-center mb-6">
                <strong class="font-bold">¡Aviso Importante!</strong> Esta es una página de checkout <strong class="font-bold">simulada</strong>. No se procesarán pagos reales ni se recopilará información sensible. Es solo para demostración.
            </p>

            <form id="checkoutForm" class="space-y-8">
                <!-- Sección de Información de Envío -->
                <div>
                    <h2 class="text-2xl font-bold text-emerald-700 mb-6 border-b pb-3 border-gray-200">1. Datos de Envío y Contacto</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div>
                            <label for="nombre" class="block text-gray-700 text-sm font-bold mb-2">Nombre Completo:</label>
                            <input type="text" id="nombre" name="nombre" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="Tu Nombre y Apellido" required>
                        </div>
                        <div>
                            <label for="email" class="block text-gray-700 text-sm font-bold mb-2">Email:</label>
                            <input type="email" id="email" name="email" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="tu@email.com" required>
                        </div>
                        <div>
                            <label for="telefono" class="block text-gray-700 text-sm font-bold mb-2">Teléfono:</label>
                            <input type="tel" id="telefono" name="telefono" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="Ej: +54 9 11 XXXXXXXX" required>
                        </div>
                        <div>
                            <label for="direccion" class="block text-gray-700 text-sm font-bold mb-2">Dirección:</label>
                            <input type="text" id="direccion" name="direccion" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="Calle y número" required>
                        </div>
                        <div>
                            <label for="ciudad" class="block text-gray-700 text-sm font-bold mb-2">Ciudad:</label>
                            <input type="text" id="ciudad" name="ciudad" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="Tu Ciudad" required>
                        </div>
                        <div>
                            <label for="provincia" class="block text-gray-700 text-sm font-bold mb-2">Provincia:</label>
                            <input type="text" id="provincia" name="provincia" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="Tu Provincia" required>
                        </div>
                        <div>
                            <label for="codigo_postal" class="block text-gray-700 text-sm font-bold mb-2">Código Postal:</label>
                            <input type="text" id="codigo_postal" name="codigo_postal" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="Ej: C1000AAA" required>
                        </div>
                    </div>
                </div>

                <!-- Sección de Método de Pago -->
                <div>
                    <h2 class="text-2xl font-bold text-emerald-700 mb-6 border-b pb-3 border-gray-200">2. Método de Pago</h2>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <!-- Mercado Pago -->
                        <label for="mpago" class="payment-method-card flex items-center space-x-4">
                            <input type="radio" id="mpago" name="payment_method" value="mercado_pago" class="form-radio text-emerald-600 h-5 w-5" checked>
                            <img src="https://placehold.co/80x30/f0f0f0/333?text=Mercado+Pago" alt="Mercado Pago Logo" class="h-8 object-contain">
                            <span class="font-semibold text-lg">Mercado Pago</span>
                        </label>
                        <!-- Tarjeta de Crédito -->
                        <label for="tarjeta" class="payment-method-card flex items-center space-x-4">
                            <input type="radio" id="tarjeta" name="payment_method" value="tarjeta_credito" class="form-radio text-emerald-600 h-5 w-5">
                            <img src="https://placehold.co/80x30/f0f0f0/333?text=Tarjetas" alt="Tarjetas de Crédito Logo" class="h-8 object-contain">
                            <span class="font-semibold text-lg">Tarjeta de Crédito</span>
                        </label>
                        <!-- PayPal -->
                        <label for="paypal" class="payment-method-card flex items-center space-x-4">
                            <input type="radio" id="paypal" name="payment_method" value="paypal" class="form-radio text-emerald-600 h-5 w-5">
                            <img src="https://placehold.co/80x30/f0f0f0/333?text=PayPal" alt="PayPal Logo" class="h-8 object-contain">
                            <span class="font-semibold text-lg">PayPal</span>
                        </label>
                    </div>

                    <!-- Detalles de Tarjeta de Crédito (solo si se selecciona) -->
                    <div id="creditCardDetails" class="mt-6 p-6 bg-gray-50 rounded-lg border border-gray-200 hidden">
                        <h3 class="text-xl font-bold text-gray-700 mb-4">Datos de la Tarjeta</h3>
                        <div class="space-y-4">
                            <div>
                                <label for="numero_tarjeta" class="block text-gray-700 text-sm font-bold mb-2">Número de Tarjeta:</label>
                                <input type="text" id="numero_tarjeta" name="numero_tarjeta" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="XXXX XXXX XXXX XXXX">
                            </div>
                            <div class="grid grid-cols-2 gap-4">
                                <div>
                                    <label for="vencimiento" class="block text-gray-700 text-sm font-bold mb-2">Fecha de Vencimiento (MM/AA):</label>
                                    <input type="text" id="vencimiento" name="vencimiento" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="MM/AA">
                                </div>
                                <div>
                                    <label for="cvv" class="block text-gray-700 text-sm font-bold mb-2">CVV:</label>
                                    <input type="text" id="cvv" name="cvv" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="XXX">
                                </div>
                            </div>
                            <div>
                                <label for="nombre_titular" class="block text-gray-700 text-sm font-bold mb-2">Nombre del Titular:</label>
                                <input type="text" id="nombre_titular" name="nombre_titular" class="shadow appearance-none border rounded-xl w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-emerald-500" placeholder="Como aparece en la tarjeta">
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Resumen del Pedido (Simulado) -->
                <div>
                    <h2 class="text-2xl font-bold text-emerald-700 mb-6 border-b pb-3 border-gray-200">3. Resumen del Pedido</h2>
                    <div class="bg-gray-50 p-6 rounded-lg space-y-3">
                        <div class="flex justify-between text-lg">
                            <span>1x Kit AquaFlex Pro</span>
                            <span>$16.000</span>
                        </div>
                        <div class="flex justify-between text-lg text-emerald-700 font-semibold">
                            <span>Envío</span>
                            <span>¡GRATIS!</span>
                        </div>
                        <div class="flex justify-between text-2xl font-bold text-emerald-800 pt-4 border-t border-gray-200">
                            <span>Total</span>
                            <span>$16.000</span>
                        </div>
                    </div>
                </div>

                <button type="submit" class="btn-primary w-full py-4 text-2xl shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all duration-300">
                    Finalizar Compra
                </button>
            </form>
        </div>
    </main>

    <!-- Modal de Confirmación de Pago / Aviso de Integración -->
    <div id="paymentModal" class="modal">
        <div class="modal-content">
            <span class="close-button" onclick="closeModal()">&times;</span>
            <div class="text-center">
                <div class="text-6xl text-red-500 mb-6">⚠️</div>
                <h2 class="text-3xl font-bold text-red-700 mb-4">¡Atención! Proceso de Pago</h2>
                <p class="text-lg text-gray-700 mb-6">
                    Para que el pago sea <strong class="font-bold">real y seguro</strong>, esta página requiere una integración con un <strong class="font-bold">servidor backend</strong> y las APIs de las pasarelas de pago (Mercado Pago, tarjetas, PayPal).
                </p>
                <p class="text-md text-gray-600 mb-6">
                    Actualmente, esta es una <strong class="font-bold">simulación</strong>. No se ha procesado ningún pago real ni se ha guardado tu información.
                </p>
                <p class="text-md text-gray-600">
                    Si deseas implementar un sistema de pago real, necesitarás un desarrollo de backend y seguridad profesional.
                </p>
                <button onclick="window.location.href='index.html'" class="btn-primary mt-8 px-6 py-3 bg-red-600 hover:bg-red-700">Entendido, Volver al Inicio</button>
            </div>
        </div>
    </div>

    <script>
        const checkoutForm = document.getElementById('checkoutForm');
        const paymentMethodRadios = document.querySelectorAll('input[name="payment_method"]');
        const creditCardDetails = document.getElementById('creditCardDetails');
        const paymentModal = document.getElementById('paymentModal'); // Changed ID to be more generic

        // Function to show/hide credit card details based on selection
        paymentMethodRadios.forEach(radio => {
            radio.addEventListener('change', () => {
                if (document.getElementById('tarjeta').checked) {
                    creditCardDetails.classList.remove('hidden');
                    // Make credit card fields required when selected
                    document.getElementById('numero_tarjeta').setAttribute('required', 'true');
                    document.getElementById('vencimiento').setAttribute('required', 'true');
                    document.getElementById('cvv').setAttribute('required', 'true');
                    document.getElementById('nombre_titular').setAttribute('required', 'true');
                } else {
                    creditCardDetails.classList.add('hidden');
                    // Remove required attribute when not selected
                    document.getElementById('numero_tarjeta').removeAttribute('required');
                    document.getElementById('vencimiento').removeAttribute('required');
                    document.getElementById('cvv').removeAttribute('required');
                    document.getElementById('nombre_titular').removeAttribute('required');
                }
            });
        });

        // Add 'selected' class to the parent label when a radio button is checked
        paymentMethodRadios.forEach(radio => {
            radio.closest('label').classList.remove('selected'); // Remove from all initially
            if (radio.checked) {
                radio.closest('label').classList.add('selected');
            }
            radio.addEventListener('change', () => {
                paymentMethodRadios.forEach(r => r.closest('label').classList.remove('selected'));
                radio.closest('label').classList.add('selected');
            });
        });


        // Handle form submission (simulated)
        checkoutForm.addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent actual form submission

            // Basic validation (can be more robust)
            const requiredFields = checkoutForm.querySelectorAll('[required]');
            let allFieldsFilled = true;
            requiredFields.forEach(field => {
                if (!field.value.trim()) {
                    allFieldsFilled = false;
                    field.style.borderColor = '#ef4444'; // Highlight empty fields
                } else {
                    field.style.borderColor = ''; // Reset border
                }
            });

            if (!allFieldsFilled) {
                // In a real app, you'd show a user-friendly error message
                console.error('Por favor, completa todos los campos requeridos.');
                return;
            }

            // Show the modal explaining real payment integration
            showModal();
        });

        // Modal functions
        function showModal() {
            paymentModal.style.display = 'flex';
        }

        function closeModal() {
            paymentModal.style.display = 'none';
        }

        // Close modal if clicked outside (optional)
        window.addEventListener('click', function(event) {
            if (event.target == paymentModal) {
                closeModal();
            }
        });
    </script>
</body>
</html>
