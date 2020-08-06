## Create a special "matrix" object that can cache its inverse
makeCacheMatrix <- function (m = matrix() ) {
## Initialize the inverse funtion
    i <- NULL
    set <- function(matrix ) {
            m <<- matrix
            i <<- NULL
}
    get <- function() {
    	m
}
    setInverse <- function(inverse) {
        i <<- inverse
}
    getInverse <- function() {
        i
## Return the list of the methods
    list(set = set, get = get,
         setInverse = setInverse,
         getInverse = getInverse)
}

## A function to computes the inverse of the special "matrix" returned by makeCacheMatrix above. 
## If the inverse has already been calculated (and the matrix has not changed), then the cachesolve 
## should retrieve the inverse from the cache.

m <- x$getInverse()
if( !is.null(m) ) {
     message("getting cached data")
     return(m)
}
data <- x$get()
m <- solve(data) %*% data
x$setInverse(m)

## Return the matrix
    m
}
