var productIds = [
    "51119013",
    "51119443",
    "45038518",
    "54591332",
    "37990657"
];

productIds.forEach(function(productId) {
    $.ajax("https://economy.roblox.com/v1/purchases/products/" + productId, {
        method: "POST",
        headers: {"X-CSRF-TOKEN": Roblox.XsrfToken.getToken()},
        dataType: "json",
        data: {
            expectedCurrency: 0,
            expectedPrice: 0,
            expectedSellerId: 1
        },
        success: function(data) {
            if (data.purchased) {
                console.log("Bought", data.assetName);
            }
        }
    });
});
