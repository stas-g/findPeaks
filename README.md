# findPeaks

A repo for a function I posted as part of my answer to a [quesiton about peak detection](http://stats.stackexchange.com/questions/22974/how-to-find-local-peaks-valleys-in-a-series-of-data/164830#164830) on StackExchange.

The function takes an ordered sequence (vector) of values `x` and a number `m` and returns a vector of indices of local peaks in `x`. A (local) peak is defined as a point such that `m` points either side of it has a lower or equal value to it, i.e. an element ![](http://www.sciweavers.org/download/Tex2Img_1492645732.jpg) such that: 

![](http://www.sciweavers.org/download/Tex2Img_1492646181.jpg)

 Thus, `m`  can be used adjust the sensitivity of the peak detection procedure: larger `m` will result in fewer peaks, whilst smaller values of `m` will result in more peaks found. 

```r
set.seed(321)
w <- abs(rnorm(1000))
w[sample(1 : 1000, 25)] <- rpois(25, 5)
w[sample(1 : 1000, 25)] <- rpois(25, 10)

par(mfrow = c(2, 2))
for(k in c(10, 20, 50, 250)){
	p <- find_peaks(w, m = k)
	plot(w, type = 'l', main = paste0('m = ', k))
	points(p, w[p], col = 'red', pch = 19)
}
```

![GitHub Logo](https://raw.githubusercontent.com/stas-g/findPeaks/master/find_peaks.pdf)
