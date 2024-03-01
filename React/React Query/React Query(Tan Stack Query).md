## [Tanstack Query Over view](https://www.youtube.com/watch?v=lVLz_ASqAio)

![[Pasted image 20231004111611.png]]

Implementing Tan Stack Query
![[Pasted image 20231004112740.png]]
Import and wrap App in <QueryClientProvider></QueryClientProvider >, create a queryClient. To use Dev tools just add single <ReactQueryDevtools />

UseQuery is where the magic happens
![[Pasted image 20231004113236.png]]
Behind the getPosts
![[Pasted image 20231004113615.png]]
Query Key is a unique identifier for the route
![[Pasted image 20231004114124.png]]
the queryKey is the connection to the data. Status and error are just the most common values that can be returned.(see )
getPosts![[Pasted image 20231109134402.png]]
React Query caches the results of the query in background and shows the results of updated query when they become available.

 

useMutation takes a mutate function
![[Pasted image 20231004122929.png]]![[Pasted image 20231004123428.png]]
getPostPaginated creates paginate data
![[Pasted image 20231004123709.png]]
##### KeepPreviousData: true 
forces React Query to keep data facilitating next/back functionality without resubmitting the query.

##### fetchStatus allow Tan Stack Query to display when it has to fetch the data
![[Pasted image 20231004124550.png]]
![[Pasted image 20231004124503.png]]
useInfiniteQuery
![[Pasted image 20231004124852.png]]
