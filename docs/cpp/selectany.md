---
title: selectany | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- selectany_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d8b4a1a78fb8231d407e60ded2c6dea3f7c891d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="selectany"></a>selectany
**Dotyczące firmy Microsoft**  
  
 Informuje kompilator, że element zadeklarowane danych globalnych (zmiennej lub obiektu) jest pobranie wszystkich COMDAT (spakowanych funkcji).  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec( selectany ) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 W momencie łącza Jeśli wiele definicji COMDAT są widoczne, konsolidator wybiera jeden i odrzuca wszystkie pozostałe. Jeśli opcja konsolidatora [/OPT:REF](../build/reference/opt-optimizations.md) (optymalizacje) jest zaznaczone, a następnie nastąpi eliminacji COMDAT Aby usunąć wszystkie elementy danych bez odwołań w danych wyjściowych konsolidatora.  
  
 Konstruktory i przypisanie funkcji globalnej lub statycznej metody w deklaracji nie twórz odwołaniem i nie zapobiega /OPT:REF eliminacji. Efekty uboczne z taki kod nie powinien zależne od, gdy nie występują żadne inne relacje z danymi.  
  
 W przypadku obiektów dynamicznie zainicjowany, globalnych `selectany` spowoduje odrzucenie kod inicjujący nieużywane obiektu, a także.  
  
 Element danych globalnych normalnie mogą być inicjowane tylko raz w projekcie plik EXE lub DLL. `selectany`może służyć inicjowania danych globalnych, zdefiniowane przez nagłówków, gdy ten sam nagłówek pojawi się w więcej niż jeden plik źródłowy. `selectany`jest dostępna w C i C++ kompilatory.  
  
> [!NOTE]
>  `selectany`można zastosować tylko do rzeczywistego inicjowania elementów danych globalnych, które są widoczne na zewnątrz.  
  
## <a name="example"></a>Przykład  
 Ten kod przedstawia sposób użycia `selectany` atrybutu:  
  
```  
//Correct - x1 is initialized and externally visible   
__declspec(selectany) int x1=1;  
  
//Incorrect - const is by default static in C++, so   
//x2 is not visible externally (This is OK in C, since  
//const is not by default static in C)  
const __declspec(selectany) int x2 =2;  
  
//Correct - x3 is extern const, so externally visible  
extern const __declspec(selectany) int x3=3;  
  
//Correct - x4 is extern const, so it is externally visible  
extern const int x4;  
const __declspec(selectany) int x4=4;  
  
//Incorrect - __declspec(selectany) is applied to the uninitialized  
//declaration of x5  
extern __declspec(selectany) int x5;  
  
// OK: dynamic initialization of global object  
class X {  
public:  
X(int i){i++;};  
int i;  
};  
  
__declspec(selectany) X x(1);  
```  
  
## <a name="example"></a>Przykład  
 Ten kod przedstawia sposób użycia `selectany` atrybutu, aby upewnić się, gdy używany jest zwijaniu sekcji COMDAT danych [/OPT: ICF](../build/reference/opt-optimizations.md) — opcja konsolidatora. Należy pamiętać, że dane muszą być oznaczone `selectany` i umieszczony w **const** sekcji (tylko do odczytu). Należy jawnie określić sekcji tylko do odczytu.  
  
```  
// selectany2.cpp  
// in the following lines, const marks the variables as read only  
__declspec(selectany) extern const int ix = 5;  
__declspec(selectany) extern const int jx = 5;  
int main() {  
   int ij;  
   ij = ix + jx;  
}  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)