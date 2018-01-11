---
title: "Podwójna konwersja bitowa adresów (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1d905f962af6a9cf07ecb0926503fc24e21c0136
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="double-thunking-c"></a>Podwójna konwersja bitowa adresów (C++)
Podwójna konwersja bitowa adresów oznacza spadek wydajności, który może wystąpić, gdy wywołanie funkcji w wywołaniach kontekstu zarządzanych, Visual C++ zarządzane funkcji i gdzie program wykonywania wywołuje punkt wejścia natywnej funkcji w celu wywołania funkcji zarządzanych. W tym temacie omówiono, gdzie występuje podwójna konwersja bitowa adresów i jak można uniknąć, aby zwiększyć wydajność.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie podczas kompilowania za pomocą **/CLR**, definicji funkcji zarządzanego umożliwia kompilatorowi Generowanie zarządzany punkt wejścia, a punkt wejścia natywnego. Dzięki temu zarządzanych funkcja wywoływana z miejsc wywołania natywnych i zarządzanych. Jednak jeśli istnieje punkt wejścia natywnego, może być punkt wejścia dla wszystkich wywołań funkcji. Jeśli funkcji wywołującej jest zarządzany, punkt wejścia macierzysty będzie wywoływać zarządzany punkt wejścia. W efekcie dwóch wywołania są wymagane do wywołania funkcji (w związku z tym podwójna konwersja bitowa adresów). Na przykład funkcje wirtualne są zawsze wywoływana przez punkt wejścia natywnego.  
  
 Można nakazuje kompilatorowi nie Generowanie punktu wejścia natywnego dla funkcji zarządzanego, że funkcja będzie można wywołać tylko z zarządzanych kontekstu, za pomocą [__clrcall](../cpp/clrcall.md) konwencji wywoływania.  
  
 Podobnie w przypadku eksportowania ([dllexport i dllimport](../cpp/dllexport-dllimport.md)) funkcją zarządzaną punktu wejścia natywnego jest generowana i wywoła dowolnej funkcji, który importuje i wywołania tej funkcji za pośrednictwem punktu wejścia macierzystego. Aby uniknąć podwójna konwersja bitowa adresów w tej sytuacji, nie należy używać semantyki natywnego eksportu/importu; po prostu odwołania metadanych za pomocą `#using` (zobacz [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md)).  
  
 Kompilator został zaktualizowany tak, aby ograniczyć niepotrzebne podwójna konwersja bitowa adresów. Na przykład dowolnej funkcji z zarządzanym typem w sygnaturze (w tym typ zwracany) niejawnie zostaną oznaczone jako `__clrcall`. Aby uzyskać więcej informacji na eliminacji podwójna konwersja bitowa, zobacz [http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie pokazano, podwójna konwersja bitowa adresów. Podczas kompilacji natywnego (bez **/CLR**), wywołanie funkcji wirtualnej w `main` generuje jedno wywołanie `T`przez konstruktora kopiującego i jedno wywołanie destruktora. Podobnie jest osiągana, gdy jest zadeklarowany funkcji wirtualnej za pomocą **/CLR** i `__clrcall`. Jednak gdy właśnie skompilowano z opcją **/CLR**, wywołanie funkcji generuje wywołanie konstruktora kopiującego, ale istnieje inne wywołanie konstruktora kopiującego z powodu thunk native zarządzane.  
  
### <a name="code"></a>Kod  
  
```  
// double_thunking.cpp  
// compile with: /clr  
#include <stdio.h>  
struct T {  
   T() {  
      puts(__FUNCSIG__);  
   }  
  
   T(const T&) {  
      puts(__FUNCSIG__);  
   }  
  
   ~T() {  
      puts(__FUNCSIG__);  
   }  
  
   T& operator=(const T&) {  
      puts(__FUNCSIG__);  
      return *this;  
   }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
  
   printf("calling struct S\n");  
   pS->f(t);  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
__thiscall T::T(void)  
calling struct S  
__thiscall T::T(const struct T &)  
__thiscall T::T(const struct T &)  
__thiscall T::~T(void)  
__thiscall T::~T(void)  
after calling struct S  
__thiscall T::~T(void)  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poprzedni przykład wykazać istnienie podwójna konwersja bitowa adresów. W tym przykładzie pokazano jego skutków. `for` Pętli wywołuje funkcję wirtualną i czas wykonywania programu raportów. Najwolniejsze czas jest zgłaszany, gdy program jest skompilowana przy użyciu **/CLR**. Najszybszym czasy są zgłaszane w przypadku kompilowania kodu bez **/CLR** lub wirtualnych funkcja zadeklarowana ze `__clrcall`.  
  
### <a name="code"></a>Kod  
  
```  
// double_thunking_2.cpp  
// compile with: /clr  
#include <time.h>  
#include <stdio.h>   
  
#pragma unmanaged  
struct T {  
   T() {}  
   T(const T&) {}  
   ~T() {}  
   T& operator=(const T&) { return *this; }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
   clock_t start, finish;  
   double  duration;  
   start = clock();  
  
   for ( int i = 0 ; i < 1000000 ; i++ )  
      pS->f(t);  
  
   finish = clock();  
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);  
   printf( "%2.1f seconds\n", duration );  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)