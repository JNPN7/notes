# Functional Programming
* Pure (mathematical) function
* Immutable data
* Declarative
* Easy to verify
* Lazy Evalutation i.e. evalutate only needed
* Loops do not exists in haskell

## Interactive mode:
Command: ghci
```terminal
$ ghci
ghci> :t 'a'  -- returns type
'a' :: Char
```


#### Function:
* Function defination
```haskell
func_name arg1 arg2 ... argn = <expr>
```
* Function call
```haskell
func_name arg1 arg2 ... argn
```
* Example
```haskell
in_range max min x = 
	x >= min && x <= max

in_range 5 2 3 -- True

in_range 9 3 1 -- False
```
* **Higher Order Function:** function which has function as an argument
```haskell
app :: (a -> b) -> a -> b
app f x = f x

app (\x -> x+1) 1 -- higher order + anonymous
	=> 2
```
* **Anonymous Function:** function with no name
```haskell
\<args> -> <expr>

(\x y z -> x+y+z) 1 2 3
	=> 6
```


#### Types:
* Defining types: 
	* name :: <_type_>
 * Example
```haskell
x :: Integer
x = 8

y :: Bool
y = True

z :: Float
z = 1.4354

in_range :: Integer -> Integer -> Integer -> Bool
in_range max min x = x >= min && x <= max
```

#### Function bindings
* let
```haskell
in_range max min x =
	let in_lower_bound = min <= x
		in_upper_bound = max >= x
	in 
	in_lower_bound && in_upper_bound
```
* where
```haskell
in_range max min x = ilb && iub
	where
		ilb = min <= x
		iub = max >= x
```

#### Recursion
```haskell
fac n =
	if n <= 1 then
		1
	else
		n * fac (n - 1)
```

#### Guards
```haskell
fac n
	n <= 1    = 1
	otherwise = n * fac (n - 1)
```

#### Case
```haskell
case expression of pattern -> result  
                   pattern -> result  
                   pattern -> result  
                   ...
head' :: [a] -> a  
head' xs = case xs of [] -> error "No head for empty lists!"  
                      (x:_) -> x
```

#### What
```haskell
describeList :: [a] -> String  
describeList xs = "The list is " ++ what xs  
    where what [] = "empty."  
          what [x] = "a singleton list."  
          what xs = "a longer list."
```

#### Accumulators
```haskell
fac n =  aux n 1
	where
		aux n acc
			n <= 1    = acc 
			otherwise = aux (n - 1) (n * acc)
```

#### Pattern Matching
```haskell
is_zero 0 = True
is_zero _ = False
```

#### Lists
```ghci
> 1:2:3:4:5:[]
[1, 2, 3, 4, 5]
```
* Generating list:
```haskell
asc :: Int -> Int -> [Int]
asc n m
	m < n  = []
	m == n = [m]
	m > n  = n : asc (n+1) m
```

* Functions on lists
``` haskell
import Data.List

head :: [a] -> a
head [1, 2, 3, 4, 5]
	=> 1
	
tail :: [a] -> [a]
tail [1, 2, 3, 4, 5]
	=> [2, 3, 4, 5]

length :: [a] -> Int
length [1, 2, 3, 4, 5]
	=> 5

init :: [a] -> [a]
init [1, 2, 3, 4, 5]
	=> [1, 2, 3, 4]

null :: [a] -> Bool
null []
	=> True
null [1, 2, 3, 4, 5]
	=> False

and :: [Bool] -> Bool
and [True, False, True]
	=> False

or :: [Bool] -> Bool
or [True, False, True]
	=> True
```

* List Comprehension
```haskell
[2*x | x <- [1, 2, 3]]
	=> [2, 4, 6]

[2*x | x <- [1, 2, 3], x > 1]
	=> [4, 6]

[<gen> | <elem> <- <list>, ..., <guard>, ...]

[(x, y) | x <- [1, 2, 3], y <- ['a', 'b']]
	=> [(1, 'a'), (1, 'b'), (2, 'a'), (2, 'b'), (3, 'a'), (3, 'b')]
```

* Tuples
```haskell
addTuples :: [(Int, Int)] -> [Int]
addTuples xs = [x+y | (x, y) <- xs]
```

#### Map
```haskell
map :: (a -> b) -> [a] -> [b]

map (\x -> x+1) [1, 2, 3, 4]
	=> [2, 3, 4, 5]

map (\(x, y) -> x+y) [(1, 2), (2, 3)]
	=> [3, 5]
```

#### Filter
```haskell
filter :: (a -> Bool) -> [a] -> [a]

filter (\x -> x > 2) [1, 2, 3, 4]
	=> [3, 4]
```

#### Curring
```haskell
f :: a -> b -> c -> d
f :: a -> (b -> (c -> d))
```

#### Composition (.)
```haskell
(.) :: (b -> c) -> (a -> b) -> a -> c
descSort = reverse . sort
descSort = (\x -> reverse (sort x))
descSort x = reverse (sort x)

-- Practical example
map2D :: (a -> b) -> [[a]] -> [[b]]
map2D = map . map
```

#### Dollar Sign [make code cleaner]
```haskell
($) :: (a -> b) -> a -> b

f xs = map (\x -> x+1) (filter (\x -> x>1)) xs
f xs = map (\x -> x+1) $ filter (\x -> x>1) xs
```

#### Folding
Big O: O(N)
* foldr: Fold right
```haskell
foldr :: (a -> b -> b) -> b -> [a] -> b

foldr (+) a [x1, x2, ..., xn] = x1 + x2 + .. + xn + a

sum = foldr (+) 0
and = foldr (&&) True

-- Own foldr
foldr_own = (\elem acc -> <term>) <start_acc> <list>

count e = foldr (\x acc -> if e==x then acc+1 else acc) 0
count 1 [1, 2, 3, 1, 54, 4]
```
* foldl: Fold left
```haskell
foldr (\elem acc -> <term>) <start_acc> <list>

foldl (\acc elem -> <term>) <start_acc> <list>
```
* Use case of foldl
```haskell
rev :: [a] -> [a]
rev = foldl (\acc x -> x : acc) []
rev = foldl (flip (:)) []
```

![alt foldr vs foldl](/assets/haskell/foldl_vs_foldr.png)
![alt foldr](/assets/haskell/foldr.png)
![alt foldr](/assets/haskell/foldl.png)
#### Datatypes
```haskell
data Name =
	Constructor1 <args>
	Constructor2 <args>
	...

data Color =
	Red | Orange | Yellow | Green | Blue

data PeaNum =
	Succ PeaNum | Zero

four :: PeaNum
four = Succ $ Succ $ Succ $ Zero

data Calculation =
	Add Int Int | Sub Int Int | Mul Int Int | Div Int Int

calc :: Caluclation -> Int
calc (Add x y) = x + y
calc (Sub x y) = x - y
calc (Mul x y) = x * y
calc (Div x y) = div x y -- x / y

data Tree a = Leaf | Node (Tree a) a (Tree a)

tree :: Tree int
tree = Node(Node Leaf 1 Leaf) 2 (Node (Node Leaf 3 Leaf) 4 Leaf)
```

#### Records
```haskell
data Person = Person String Int
-- Better one
data Person = Person { name :: String, age :: Int}

-- Created by compiler
-- name :: Person -> String
-- age :: Person -> Int

greet :: Person -> [Char]
greet person = "Hi " ++ name person
greet (Person name _) = "Hi " ++ name

-- Can have different contructors
data Point = 
	D2 { x :: Int, y :: Int }
	D3 { x :: Int, y :: Int , z :: Int}
x (D2 1 2)
	=> 1
x (D3 1 2 3)
	=> 1
```

#### Typeclasses
```haskell
(+) :: Num a => a -> a -> a -> a
-- a has to have an instance of the Num typeclass
-- ghci> :info Num
```
----- TODO! -----

#### Maybe
```haskell
data Maybe a = Nothing | Just a 

safediv :: Integral a => a -> a -> Maybe a
safediv a b =
	if b == 0 then Nothing else Just $ div a b

-- fromMaybe
fromMaybe :: a -> Maybe a -> a
fromMaybe 3.1243 (Nothing)
	=> 3.1243
fromMaybe 3.1243 (Just 2.1243)
	=> 2.1243
```










## Exercises:
* 1.
```
#Create a function that returns a reverse of a given list 
Input : [1,2,3] 
Output : [3,2,1] 
Definition: reverse :: [a] -> [a]
```
Solution
```haskell
rev :: [a] -> [a]
-- Way first
--rev [] = []
--rev (x:xs) = rev xs ++ [x]

-- Way second
--rev [] = []
--rev x = last x : init x

-- Way third
rev = foldl (\acc x -> x : acc) []

main = print (rev [1, 2, 3])
```

* 2.
```
#Create a function that returns all the prefixes of the given list 
Input : [1,2,3] 
Output : [[1], [1,2], [1,2,3]] 
Definition: prefixes :: [a] -> [[a]]
```
Solution
```haskell
prefixes :: [a] -> [[a]]
prefixes = foldr (\x acc -> [x] : (map (\a -> x : a) acc)) []

main = print (prefixes [1, 2, 3])
```

* 3. Write a data type Complex to represent complex numbers of the form a + b\*i. Write its Num instance.
```haskell
data Complex = Complex { real      :: Double
                       , imaginary :: Double
                       } deriving Show

printComplexNum :: Complex -> [Char]
printComplexNum complex = show (real complex) ++ " + " ++ show (imaginary complex) ++ "i"

main :: IO ()
main = do
    let complex_num = Complex {real = 2.32, imaginary = 1.34}
    print (printComplexNum complex_num)
```

* 4. Write a function that accepts a list of integers as an input and return the sum. The output datatype should be Maybe Int. If the list is empty return Nothing.
```haskell
summaybe [] = Nothing
summaybe x = Just $ foldr (+) 0 x

main = print (summaybe [1, 2])
```


## Excersice 2:
Given the class Bucket, write instances for list [] , Maybe and Either (both ways).  

```haskell
class Bucket f where
 switch :: (a -> b) -> f a -> f b
```
Solution:
```haskell
class Bucket f where
    switch :: (a -> b) -> f a -> f b

--instance Bucket [] where
--  switch = map

instance Bucket [] where
    switch f [] = []
    switch f (x:xs) = f x : switch f xs

instance Bucket Maybe where
    switch f Nothing = Nothing
    switch f (Just a) = Just $ f a

instance Bucket (Either a) where
    switch f (Right b) = Right $ f b
    switch f (Left b) = Left b

--instance Bucket (Either a) where
--    switch f (Left b) = Left $ f b
--    switch f (Right b) = Right b
```

**2.** Guess the output of this code statement and try to reason about your output.

```haskell
f = (+) <$> (*2) <*> (+10)
answer= f 3
```
Solution:
* The  (+) function takes two inputs
* <\*> separater two function in which + operation need to be performed at end
* The (\*2) function takes 3 as an argument 
* The (+10) function takes 3 as an argument
* The upper funtion becomes:
	* (+) ((\*2) 3) ((+10) 3)
* The function can also be written as:
	* f x = (+) ((\*2) x) ((+10) x)


#### intersperse
```haskell
ghci> intersperse '.' "MONKEY"  
"M.O.N.K.E.Y"  
ghci> intersperse 0 [1,2,3,4,5,6]  
[1,0,2,0,3,0,4,0,5,0,6]
```

#### intercalate
```haskell
ghci> intercalate " " ["hey","there","guys"]  
"hey there guys"  
ghci> intercalate [0,0,0] [[1,2,3],[4,5,6],[7,8,9]]  
[1,2,3,0,0,0,4,5,6,0,0,0,7,8,9]
```

#### transpose
```haskell
ghci> transpose [[1,2,3],[4,5,6],[7,8,9]]  
[[1,4,7],[2,5,8],[3,6,9]]  
ghci> transpose ["hey","there","guys"]  
["htg","ehu","yey","rs","e"]  
```

#### concat
```haskell
ghci> concat ["foo","bar","car"]  
"foobarcar"  
ghci> concat [[3,4,5],[2,3,4],[2,1,1]]  
[3,4,5,2,3,4,2,1,1]
```

#### concatMap - first map then concat
```haskell
ghci> concatMap (replicate 4) [1..3]  
[1,1,1,1,2,2,2,2,3,3,3,3]
```

#### any | all
```haskell
ghci> any (==4) [2,3,5,6,1,4]  
True  
ghci> all (>4) [6,9,10]  
True  
ghci> all (`elem` ['A'..'Z']) "HEYGUYSwhatsup"  
False  
ghci> any (`elem` ['A'..'Z']) "HEYGUYSwhatsup"  
True 
```

#### iterate
```haskell
ghci> take 10 $ iterate (*2) 1  
[1,2,4,8,16,32,64,128,256,512]  
ghci> take 3 $ iterate (++ "haha") "haha"  
["haha","hahahaha","hahahahahaha"]
```

#### splitAt
```haskell
ghci> splitAt 3 "heyman"  
("hey","man")  
ghci> splitAt 100 "heyman"  
("heyman","")  
ghci> splitAt (-3) "heyman"  
("","heyman")  
ghci> let (a,b) = splitAt 3 "foobar" in b ++ a  
"barfoo"
```

#### takeWhile
```haskell
ghci> takeWhile (>3) [6,5,4,3,2,1,2,3,4,5,4,3,2,1]  
[6,5,4]  
ghci> takeWhile (/=' ') "This is a sentence"  
"This"
```

#### dropWhile
```haskell
ghci> dropWhile (/=' ') "This is a sentence"  
" is a sentence"  
ghci> dropWhile (<3) [1,2,2,2,3,4,5,4,3,2,1]  
[3,4,5,4,3,2,1]
```

#### span
```haskell
ghci> let (fw, rest) = span (/=' ') "This is a sentence" in "First word:" ++ fw ++ ", the rest:" ++ rest  
"First word: This, the rest: is a sentence"
```

#### break
```haskell
ghci> break (==4) [1,2,3,4,5,6,7]  
([1,2,3],[4,5,6,7])  
ghci> span (/=4) [1,2,3,4,5,6,7]  
([1,2,3],[4,5,6,7])
```

#### sort
```haskell
ghci> sort [8,5,3,2,1,6,4,2]  
[1,2,2,3,4,5,6,8]  
ghci> sort "This will be sorted soon"  
"    Tbdeehiillnooorssstw"
```

#### group
```haskell
ghci> group [1,1,1,1,2,2,2,2,3,3,2,2,2,5,6,7]  
[[1,1,1,1],[2,2,2,2],[3,3],[2,2,2],[5],[6],[7]]
```

#### inits & tails
```haskell
ghci> inits "w00t"  
ghci> tails "w00t"  
["w00t","00t","0t","t",""]  
ghci> let w = "w00t" in zip (inits w) (tails w)  
[("","w00t"),("w","00t"),("w0","0t"),("w00","t"),("w00t","")]
```

#### isInfixOf -> subset
```haskell
ghci> "cat" `isInfixOf` "im a cat burglar"  
True  
ghci> "Cat" `isInfixOf` "im a cat burglar"  
False
```

#### isPrefixOf -> at start & isSuffixOf -> at end
```haskell
ghci> "hey" `isPrefixOf` "hey there!"  
True  
ghci> "hey" `isPrefixOf` "oh hey there!"  
False  
ghci> "there!" `isSuffixOf` "oh hey there!"  
True  
ghci> "there!" `isSuffixOf` "oh hey there"  
False
```

#### partition
```haskell
ghci> partition (`elem` ['A'..'Z']) "BOBsidneyMORGANeddy"  
("BOBMORGAN","sidneyeddy")  
ghci> partition (>3) [1,3,5,6,3,2,1,0,3,7]  
([5,6,7],[1,3,3,2,1,0,3])
```

#### find
```haskell
ghci> find (>4) [1,2,3,4,5,6]  
Just 5  
ghci> find (>9) [1,2,3,4,5,6]  
Nothing  
ghci> :t find  
find :: (a -> Bool) -> [a] -> Maybe a
```

#### elemIndex
```haskell
ghci> :t elemIndex  
elemIndex :: (Eq a) => a -> [a] -> Maybe Int  
ghci> 4 `elemIndex` [1,2,3,4,5,6]  
Just 3  
ghci> 10 `elemIndex` [1,2,3,4,5,6]  
Nothing
```

#### elemIndices
```haskell
ghci> ' ' `elemIndices` "Where are the spaces?"  
[5,9,13]
```

#### findIndex
```haskell
ghci> findIndex (==4) [5,3,2,1,6,4]  
Just 5  
ghci> findIndex (==7) [5,3,2,1,6,4]  
Nothing  
ghci> findIndices (`elem` ['A'..'Z']) "Where Are The Caps?"  
[0,6,10,14]
```

#### lines -> returns list of every line
```haskell
ghci> lines "first line\nsecond line\nthird line"
["first line","second line","third line"]
```

#### unlines -> returns string from list
```haskell
ghci> unlines ["first line", "second line", "third line"]  
"first line\nsecond line\nthird line\n"
```

#### words and unwords
```haskell
ghci> words "hey these are the words in this sentence"  
["hey","these","are","the","words","in","this","sentence"]  
ghci> words "hey these           are    the words in this\nsentence"  
["hey","these","are","the","words","in","this","sentence"]  
ghci> unwords ["hey","there","mate"]  
"hey there mate"
```

#### nub -> remove duplicate elements
```haskell
ghci> nub [1,2,3,4,3,2,1,2,3,4,3,2,1]  
[1,2,3,4]  
ghci> nub "Lots of words and stuff"  
"Lots fwrdanu"
```

#### delete -> deletes first occurance
```haskell
ghci> delete 'h' "hey there ghang!"  
"ey there ghang!"  
ghci> delete 'h' . delete 'h' $ "hey there ghang!"  
"ey tere ghang!"  
ghci> delete 'h' . delete 'h' . delete 'h' $ "hey there ghang!"  
"ey tere gang!"
```

#### \\\\ -> list difference function
```haskell
ghci> [1..10] \\ [2,5,9]  
[1,3,4,6,7,8,10]  
ghci> "Im a big baby" \\ "big"  
"Im a  baby"
```

### TODO! remains | Modules






> ch 6 | modules remains
> ch 7



### Extensions:
```haskell
{-# LANGUAGE OverloadedStrings #-}
{-# LANGUAGE TypeApplications #-} -> define a type
flip parseMaybe result $ \obj -> do
        age  <- obj .: "age" 
        name <- obj .: "name"
        Just (name ++ " : " ++ show @Integer (age))
{-# LANGUAGE ShowTypeVariable #-} -> define a type another way
flip parseMaybe result $ \obj -> do
        age :: Int <- obj .: "age" 
        name <- obj .: "name"
        Just (name ++ " : " ++ show (age))
```