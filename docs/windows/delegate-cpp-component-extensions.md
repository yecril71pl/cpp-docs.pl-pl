---
title: Delegat (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- delegate_cpp
- delegate
dev_langs:
- C++
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30fd64fd37fb30c34b5d4f5901f16143fb1cd701
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="delegate--c-component-extensions"></a>delegate (C++ Component Extensions)
Deklaruje typ, który reprezentuje wskaźnik funkcji.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Środowisko wykonawcze systemu Windows i środowisko uruchomieniowe języka wspólnego obsługuje delegatów.  
  
### <a name="remarks"></a>Uwagi  
 `delegate`jest słowem kluczowym kontekstowa. Aby uzyskać więcej informacji, zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Aby wykrywać w czasie kompilacji, jeśli typ delegata, użyj `__is_delegate()` typu cechy. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 C + +/ CX obsługuje delegatów przy użyciu następującej składni.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
access  
delegate  
return-type  
delegate-type-identifier  
(  
[ parameters ]  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
 *dostęp*  
 (opcjonalnie) Dostępność delegata, która może być `public` (ustawienie domyślne) lub `private`. Prototypu funkcji można również być kwalifikowany za pomocą `const` lub `volatile` słów kluczowych.  
  
 *zwracanego typu*  
 Typ zwracany prototypu funkcji.  
  
 *Delegat typu identyfikator*  
 Nazwa typu delegowanego zadeklarowane.  
  
 *Parametry*  
 (Opcjonalnie) Typy i identyfikatory prototypu funkcji.  
  
### <a name="remarks"></a>Uwagi  
 Użyj *delegowanego typu identyfikatorów* Aby zadeklarować zdarzenie z tej samej prototypu jako pełnomocnik. Aby uzyskać więcej informacji, zobacz [delegatów (C + +/ CX)](../cppcx/delegates-c-cx.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 Środowisko uruchomieniowe języka wspólnego obsługuje delegatów przy użyciu następującej składni.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
access  
delegate  
function_declaration  
  
```  
  
### <a name="parameters"></a>Parametry  
 *dostęp*  
 (opcjonalnie) Dostępność delegata poza zestaw może być publicznych lub prywatnych.  Wartość domyślna to prywatne.  W klasie Delegat może mieć żadnych ułatwień dostępu.  
  
 *function_declaration*  
 Podpis funkcji, która może być powiązana z obiektem delegowanym. Typ zwracany delegata mogą być dowolnego typu zarządzanego. Ze względu na współdziałanie zaleca się, że typ zwracany delegata być typem ze specyfikacją CLS.  
  
 Aby zdefiniować niezwiązanego delegata, pierwszy parametr w *function_declaration* powinien być typu `this` wskaźnik dla obiekt. 
  
### <a name="remarks"></a>Uwagi  
 Obiekty delegowane są multiemisji: "wskaźnik funkcji" może być powiązana z co najmniej jednej metody w klasie zarządzanej. **Delegować** — słowo kluczowe definiuje typ delegata multiemisji za pomocą podpisu dla określonej metody.  
  
 Delegat może być powiązana również metody klasy wartości, takich jak metody statycznej.  
  
 Delegat ma następującą charakterystykę:  
  
-   Dziedziczy on z **System::MulticastDelegate**.  
  
-   Ma on konstruktora, który przyjmuje dwa argumenty: wskaźnik do zarządzanej klasy lub **NULL** (w przypadku tworzenia powiązania z metodą statyczną), a także metodę pełną określonego typu.  
  
-   Zawiera ona metodę o nazwie `Invoke`, którego podpis pasuje zadeklarowane podpis delegata.  
  
 Po wywołaniu delegata jego funkcje są nazywane w kolejności, które zostały dołączone.  
  
 Wartość zwracana delegata jest wartość zwracana z jej ostatniej funkcji dołączonych elementu członkowskiego.  
  
 Obiekty delegowane nie może być przeciążony.  
  
 Obiekty delegowane można powiązany lub niepowiązanych.  
  
 Gdy wystąpienia delegata powiązane, pierwszy argument musi być odwołanie do obiektu.  Drugi argument wystąpienia delegata są albo być adres metodę obiektu zarządzanej klasy lub wskaźnik do metody typu wartości.   Drugi argument wystąpienia delegata musi nazwy metody klasy pełnej składni zakresu i zastosować operator address-of.  
  
 W przypadku wystąpienia niezwiązanego delegata, pierwszy argument jest adres metodę obiektu zarządzanej klasy lub wskaźnik do metody typu wartości.   Argument musi nazwę metody klasy pełnej składni zakresu i zastosować operator address-of.  
  
 Podczas tworzenia delegata funkcji statyczne lub globalnych, konieczne jest tylko jeden parametr: funkcja (opcjonalnie adresu funkcji).  
  
 Aby uzyskać więcej informacji na delegatów zobacz  
  
-   [Instrukcje: definiowanie obiektów delegowanych (C++/CLI) oraz korzystanie z nich](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [Delegaty ogólne (Visual C++)](../windows/generic-delegates-visual-cpp.md)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład pokazuje, jak zadeklarować, zainicjować i wywoływać delegatów.  
  
```cpp  
// mcppv2_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare a delegate  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      Console::WriteLine("in func1 {0}", i);  
   }  
  
   void func2(int i) {  
      Console::WriteLine("in func2 {0}", i);  
   }  
  
   static void func3(int i) {  
      Console::WriteLine("in static func3 {0}", i);  
   }  
};  
  
int main () {  
   A ^ a = gcnew A;  
  
   // declare a delegate instance  
   MyDel^ DelInst;  
  
   // test if delegate is initialized  
   if (DelInst)  
      DelInst(7);  
  
   // assigning to delegate  
   DelInst = gcnew MyDel(a, &A::func1);  
  
   // invoke delegate  
   if (DelInst)  
      DelInst(8);  
  
   // add a function  
   DelInst += gcnew MyDel(a, &A::func2);  
  
   DelInst(9);  
  
   // remove a function  
   DelInst -= gcnew MyDel(a, &A::func1);  
  
   // invoke delegate with Invoke  
   DelInst->Invoke(10);  
  
   // make delegate to static function  
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);  
   StaticDelInst(11);  
}  
```  
  
 **Output**  
  
```Output  
in func1 8  
  
in func1 9  
  
in func2 9  
  
in func2 10  
  
in static func3 11  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)