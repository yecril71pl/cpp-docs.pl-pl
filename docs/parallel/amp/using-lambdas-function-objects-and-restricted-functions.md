---
title: Używanie wyrażeń lambda, obiektów funkcyjnych i funkcji z ograniczeniami | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 99c228d018402d44186efdda264d1eec83b0332f
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465974"
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Używanie wyrażeń lambda, obiektów Function i funkcji z ograniczeniami
Kod C++ AMP, który chcesz uruchomić na akceleratorze, jest określony jako argument w wywołaniu [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody. Możesz podać w wyrażeniu lambda lub obiekt funkcyjny (funktor) w roli tego argumentu. Ponadto obiekt lambda wyrażenia lub funkcja może wywołać funkcję C++ AMP z ograniczeniami. Ten temat korzysta z algorytmu dodawania tablic do zademonstrowania wyrażeń lambda, obiektów funkcyjnych i funkcji z ograniczeniami. Poniższy przykład pokazuje jest algorytm bez kodu C++ AMP. Są tworzone dwie tablice 1-wymiarowe równej długości. Odpowiadające elementy całkowite są dodawane i przechowywane w trzeciej 1-wymiarowej tablicy. C++ AMP nie jest używana.  
  
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
 
Użycie wyrażenia lambda jest najbardziej bezpośrednim sposobem wykorzystania C++ AMP do przepisania kodu.  
  
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
  
Wyrażenie lambda musi zawierać jeden parametr indeksowania i musi zawierać `restrict(amp)`. W tym przykładzie [array_view](../../parallel/amp/reference/array-view-class.md) `sum` obiekt ma rangę 1. Dlatego parametr do instrukcji lambda jest [indeksu](../../parallel/amp/reference/index-class.md) o randze 1. W czasie wykonywania, wyrażenie lambda jest wykonywane raz dla każdego elementu w [array_view](../../parallel/amp/reference/array-view-class.md) obiektu. Aby uzyskać więcej informacji, zobacz [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).  
  
## <a name="function-object"></a>Obiekt Function  
 
Za współczynnika przekazać kod akceleratora do obiektu funkcyjnego.  
  
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

Obiekt funkcji, który musi zawierać Konstruktor i przeciążenie operatora wywołania funkcji. Operator wywołania funkcji musi zawierać jeden parametr indeksowania. Wystąpienie obiektu funkcji jest przekazywany jako drugi argument [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody. W tym przykładzie trzy [array_view](../../parallel/amp/reference/array-view-class.md) obiekty są przekazywane do funkcji konstruktora obiektu. [Array_view](../../parallel/amp/reference/array-view-class.md) obiektu `sum` ma rangę 1. Dlatego parametr operatora wywołania funkcji jest [indeksu](../../parallel/amp/reference/index-class.md) o randze 1. W czasie wykonywania, funkcja jest wykonywana raz dla każdego elementu w [array_view](../../parallel/amp/reference/array-view-class.md) obiektu. Aby uzyskać więcej informacji, zobacz [wywołania funkcji](../../cpp/function-call-cpp.md) i [obiekty funkcji w standardowej bibliotece C++](../../standard-library/function-objects-in-the-stl.md).  
  
## <a name="c-amp-restricted-function"></a>Funkcji ograniczonej przez AMP C++  
 
Można dodatkowo współczynnika przekazać kod akceleratora tworząc funkcję z ograniczeniami i wywołując ją w wyrażeniu lambda lub obiekt funkcyjny. Poniższy przykład kodu pokazuje, jak wywołania funkcji z ograniczeniami z wyrażenia lambda.  
  
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
  
Funkcja z ograniczeniami musi zawierać `restrict(amp)` i są zgodne z ograniczeniami które są opisane w [ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md).  
  
## <a name="see-also"></a>Zobacz też  
 
[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
[Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)   
[Wywołanie funkcji](../../cpp/function-call-cpp.md)   
[Obiekty funkcji w standardowej bibliotece C++](../../standard-library/function-objects-in-the-stl.md)   
[ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md)