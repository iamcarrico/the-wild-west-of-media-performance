### Native Font Events

```document.fonts```

Note: We also have found that we had the most failures on Chrome, which luckily had native font events built in. When a browser has native font events, we use that over Font Face Observer to check the loading of the fonts we need on the page. By using this, we have fonts load over 98% of the time on our sites— and a very accurate knowledge of when fonts are ready for use.
