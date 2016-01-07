---
layout: default
title: "Code snippets"
date: 2016-01-07
keywords: 
published: true
---

- [F# Cheatsheet](http://dungpa.github.io/fsharp-cheatsheet/)

```fsharp
open System


[ "Tick"; "Trick"; "Track" ] 
    |> List.map (fun x -> sprintf "Hello %s" x) 
    |> List.iter (printfn "%s")

let greet = List.map (fun x -> sprintf "Hello %s" x) 
let spitout = List.iter (printfn "%s")

let qq = 
    List.map (fun x -> sprintf "Hello %s" x) >> 
    List.iter (printfn ">> %s")

[ "1"; "Trick2"; "3" ]  |> (greet >> spitout)
```


```fsharp
let negate x = x * -1 
let square x = x * x 
let print x = printfn "The number is: %d" x

let squareNegateThenPrint x = print (negate (square x)) 
let squareNegateThenPrint2 = square >> negate >> print
let ``square, negate, then print 3`` x = x |> square |> negate |> print

squareNegateThenPrint 6
squareNegateThenPrint2 7
``square, negate, then print 3`` 5
```


```
[ "Tick"; "Trick"; "Track" ] 
    |> Seq.map (fun x -> sprintf "Hello %s" x) 
    |> Seq.iter (printfn "%s")

let greet = (fun x -> sprintf "Hello %s" x) 
let print = printfn "%s"

let a = Array.map greet >> Array.iter print
let l = List.map greet >> List.iter print
let s = Seq.map greet >> Seq.iter print

[ "Tick"; "Trick"; "Track" ]  |>  Seq.map greet |> Seq.iter print
[ "Tick"; "Trick"; "Track" ]  |> (Seq.map greet >> Seq.iter print)
[ "Tick"; "Trick"; "Track" ]  |> s
[ "Tick"; "Trick"; "Track" ]  |> l
[| "Tick"; "Trick"; "Track" |]  |> a
```