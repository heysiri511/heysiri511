<!DOCTYPE html>
<script>
// Sample historical stock data (replace with your actual data)
const data = [
{ days: 1, price: 100 },
{ days: 2, price: 105 },
{ days: 3, price: 110 },
{ days: 4, price: 112 },
{ days: 5, price: 115 },
];
function calculateSlope(data) {
let sumX = 0;
let sumY = 0;
let sumXY = 0;
let sumX2 = 0;
for (const point of data) {
sumX += point.days;
sumY += point.price;
sumXY += point.days * point.price;
sumX2 += point.days * point.days;
}
const slope = (sumXY - sumX * sumY / data.length) / (sumX2 - sumX * sumX / data.length);
return slope;
}
function calculateIntercept(data, slope) {
const averageX = data.reduce((acc, point) => acc + point.days, 0) / data.length;
const averageY = data.reduce((acc, point) => acc + point.price, 0) / data.length;
const intercept = averageY - slope * averageX;
return intercept;
}
function predictPrice(days, slope, intercept) {
return slope * days + intercept;
}
// Example usage
const slope = calculateSlope(data);
const intercept = calculateIntercept(data, slope);
const predictedPrice = predictPrice(6, slope, intercept); // Predict price for day 6
console.log("Predicted price for day 6:", predictedPrice);
</script>


