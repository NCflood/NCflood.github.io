<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vista Calculators</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/17.0.2/umd/react.production.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/17.0.2/umd/react-dom.production.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/6.26.0/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap');
        body {
            font-family: 'Poppins', sans-serif;
        }
        .neon-glow {
            box-shadow: 0 0 5px #fff, 0 0 10px #fff, 0 0 15px #fff, 0 0 20px #00ffff, 0 0 35px #00ffff, 0 0 40px #00ffff, 0 0 50px #00ffff, 0 0 75px #00ffff;
        }
        .hover-scale {
            transition: all 0.3s ease-in-out;
        }
        .hover-scale:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }
    </style>
</head>
<body class="bg-gradient-to-br from-blue-900 via-purple-900 to-pink-900 flex items-center justify-center min-h-screen p-8">
    <div id="root" class="w-full max-w-7xl"></div>

    <script type="text/babel">
        const { useState } = React;

        const Input = ({ id, type, value, onChange, placeholder, readOnly }) => (
            <input
                id={id}
                type={type}
                value={value}
                onChange={onChange}
                placeholder={placeholder}
                readOnly={readOnly}
                className="w-full p-4 border-2 border-cyan-400 rounded-lg text-xl bg-gray-800 text-white focus:outline-none focus:ring-2 focus:ring-cyan-500 focus:border-transparent transition duration-300 hover-scale"
            />
        );

        const Label = ({ htmlFor, children }) => (
            <label htmlFor={htmlFor} className="block text-xl font-bold text-cyan-300 mb-2">
                {children}
            </label>
        );

        const Card = ({ children, title }) => (
            <div className="bg-gray-900 shadow-2xl rounded-xl p-6 w-full hover-scale transition duration-300 border-2 border-cyan-500 neon-glow">
                <h3 className="text-3xl font-bold mb-6 text-center text-cyan-400">{title}</h3>
                {children}
            </div>
        );

        const VistaCalculators = () => {
            const [desiredPrice, setDesiredPrice] = useState('');
            const [totalSpend, setTotalSpend] = useState('');

            const calculateBidAmount = (price) => {
                return (price * 1.15) + 2;
            };

            const calculateFinalPrice = (price) => {
                return ((price * 1.15) + 2) * 1.0725;
            };

            const calculateBidFromTotal = (total) => {
                return (total / 1.0725 - 2) / 1.15;
            };

            const bidAmount = desiredPrice ? calculateBidAmount(parseFloat(desiredPrice)).toFixed(2) : '';
            const finalPrice = desiredPrice ? calculateFinalPrice(parseFloat(desiredPrice)).toFixed(2) : '';
            const bidFromTotal = totalSpend ? calculateBidFromTotal(parseFloat(totalSpend)).toFixed(2) : '';

            return (
                <div className="flex flex-col items-center">
                    <h2 className="text-5xl font-bold mb-12 text-center text-white neon-glow p-4">Vista Calculators</h2>
                    <div className="flex flex-col md:flex-row justify-between w-full space-y-8 md:space-y-0 md:space-x-8">
                        <Card title="Calculate Bid from Desired Price">
                            <div className="space-y-4">
                                <div>
                                    <Label htmlFor="desiredPrice">Desired Price ($)</Label>
                                    <Input
                                        id="desiredPrice"
                                        type="number"
                                        value={desiredPrice}
                                        onChange={(e) => setDesiredPrice(e.target.value)}
                                        placeholder="Enter desired price"
                                    />
                                </div>
                                <div>
                                    <Label>Bid Amount ($)</Label>
                                    <Input value={bidAmount} readOnly />
                                </div>
                                <div>
                                    <Label>Final Price ($)</Label>
                                    <Input value={finalPrice} readOnly />
                                </div>
                            </div>
                        </Card>
                        <Card title="Calculate Bid from Total Spend">
                            <div className="space-y-4">
                                <div>
                                    <Label htmlFor="totalSpend">Total Spend (inc. tax) ($)</Label>
                                    <Input
                                        id="totalSpend"
                                        type="number"
                                        value={totalSpend}
                                        onChange={(e) => setTotalSpend(e.target.value)}
                                        placeholder="Enter total amount to spend"
                                    />
                                </div>
                                <div>
                                    <Label>Bid Amount ($)</Label>
                                    <Input value={bidFromTotal} readOnly />
                                </div>
                            </div>
                        </Card>
                    </div>
                </div>
            );
        };

        ReactDOM.render(<VistaCalculators />, document.getElementById('root'));
    </script>
</body>
</html>
