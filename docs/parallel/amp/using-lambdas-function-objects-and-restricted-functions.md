---
title: Za pomocą wyrażenia lambda, obiektów Function i funkcji z ograniczeniami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e3e5ab742335cfd6bb47a5105995d7339c7c36a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Używanie wyrażeń lambda, obiektów Function i funkcji z ograniczeniami
Kod C++ AMP, który ma zostać uruchomione na akceleratora jest określony jako argument w wywołaniu [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody. Wyrażenia lambda lub obiektem funkcji (obiekt) można podać jako tego argumentu. Ponadto obiektu lambda wyrażenia lub funkcję można wywołać funkcji ograniczonej przez AMP C++. W tym temacie używa nieobsługiwanego algorytmu dodanie macierzy do zaprezentowania wyrażeń lambda, obiektów function i funkcji z ograniczeniami. W poniższym przykładzie przedstawiono algorytm bez kodu C++ AMP. Są tworzone dwa tablic wielowymiarowych 1 o równej długości. Odpowiednie elementy całkowitą są dodawane i przechowywane w trzecim 1-wymiarową tablicą. C++ AMP nie jest używany.  
  
```cpp  
void CpuMethod() {  
 
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    for (int idx = 0; idx <5; idx++)  
 {  
    sumCPP[idx] = aCPP[idx] + bCPP[idx];  
 }  
 
    for (int idx = 0; idx <5; idx++)  
 {  
    std::cout <<sumCPP[idx] <<"\n";  
 }  
}  
 
```  
  
## <a name="lambda-expression"></a>Wyrażenia lambda  
 Za pomocą wyrażenia lambda jest najbardziej bezpośrednim sposobem użycia C++ AMP do ponownego pisania kodu.  
  
```cpp  
void AddArraysWithLambda() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

 
    parallel_for_each(
 sum.extent, 
 [=](index<1> idx) restrict(amp)  
 {  
    sum[idx] = a[idx] + b[idx];  
 });

 
    for (int i = 0; i <5; i++) {  
    std::cout <<sum[i] <<"\n";  
 }  
}  
 
```  
  
 Wyrażenie lambda musi zawierać jeden parametr indeksowania i musi zawierać `restrict(amp)`. W tym przykładzie [array_view —](../../parallel/amp/reference/array-view-class.md) `sum` obiekt ma randze 1. W związku z tym parametr do instrukcji lambda jest [indeksu](../../parallel/amp/reference/index-class.md) obiektu, który ma randze 1. W czasie wykonywania, wyrażenia lambda jest wykonywane raz dla każdego elementu w [array_view —](../../parallel/amp/reference/array-view-class.md) obiektu. Aby uzyskać więcej informacji, zobacz [składnia wyrażenia Lambda](../../cpp/lambda-expression-syntax.md).  
  
## <a name="function-object"></a>Obiekt Function  
 Obiekt funkcji można uwzględnić kod skrótu.  
  
```cpp  
class AdditionFunctionObject  
{  
public:  
    AdditionFunctionObject(const array_view<int, 1>& a,  
    const array_view<int, 1>& b,  
    const array_view<int, 1>& sum)  
 : a(a), b(b), sum(sum)  
 {  
 }  
 
    void operator()(index<1> idx) restrict(amp)  
 {  
    sum[idx] = a[idx] + b[idx];  
 }  
 
private:  
    array_view<int, 1> a;  
    array_view<int, 1> b;  
    array_view<int, 1> sum;  
};  
 
void AddArraysWithFunctionObject() {  
 
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

 
    parallel_for_each(
 sum.extent, 
    AdditionFunctionObject(a, b, sum));

 
    for (int i = 0; i <5; i++) {  
    std::cout <<sum[i] <<"\n";  
 }  
}  
 
```  

 Obiekt funkcja musi zawierać Konstruktor i musi zawierać przeciążenia operator wywołania funkcji. Operator wywołania funkcji musi zawierać jeden parametr indeksowania. Wystąpienie obiektu funkcji jest przekazywany jako drugi argument [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody. W tym przykładzie trzy [array_view —](../../parallel/amp/reference/array-view-class.md) obiekty są przekazywane do konstruktora obiektu funkcji. [Array_view —](../../parallel/amp/reference/array-view-class.md) obiektu `sum` ma randze 1. W związku z tym jest parametr, aby operator wywołania funkcji [indeksu](../../parallel/amp/reference/index-class.md) obiektu, który ma randze 1. W czasie wykonywania, funkcja jest wykonywana raz dla każdego elementu w [array_view —](../../parallel/amp/reference/array-view-class.md) obiektu. Aby uzyskać więcej informacji, zobacz [wywołania funkcji](../../cpp/function-call-cpp.md) i [obiekty funkcji w standardowej bibliotece C++](../../standard-library/function-objects-in-the-stl.md).  
  
## <a name="c-amp-restricted-function"></a>Funkcji ograniczonej przez AMP C++  
 Kod akceleratora można dodatkowo współczynnika tworząc ograniczeniami funkcja i wywołanie go z wyrażenia lambda lub obiektem funkcji. Poniższy przykład kodu pokazuje, jak wywołać funkcję ograniczone z wyrażenia lambda.  
  
```cpp  
void AddElementsWithRestrictedFunction(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)  
{  
    sum[idx] = a[idx] + b[idx];  
}  
 
void AddArraysWithFunction() {  
 
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    array_view<int, 1> a(5, aCPP);

    array_view<int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

 
    parallel_for_each(
 sum.extent, 
 [=](index<1> idx) restrict(amp)  
 {  
    AddElementsWithRestrictedFunction(idx, sum, a, b);

 });

 
    for (int i = 0; i <5; i++) {  
    std::cout <<sum[i] <<"\n";  
 }  
}  
 
```  
  
 Funkcja ograniczona musi zawierać `restrict(amp)` i są zgodne z ograniczeniami, które zostały opisane w [ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)   
 [Wywołania funkcji](../../cpp/function-call-cpp.md)   
 [Obiekty funkcji w standardowej bibliotece C++](../../standard-library/function-objects-in-the-stl.md)   
 [ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md)

