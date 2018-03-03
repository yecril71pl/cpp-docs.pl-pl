---
title: Wylicz klasy (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 876cab344f1177000f63740ca6c33bc1db1afefe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="enum-class--c-component-extensions"></a>enum class (C++ Component Extensions)
Deklaruje wyliczenie w zakresie przestrzeni nazw, który jest zdefiniowany przez użytkownika typ zawierający zestaw o nazwie moduły wyliczające stałe nazwane.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Uwagi**  
  
 C + +/ CX i C + +/ Obsługa interfejsu wiersza polecenia `public enum class` i `private enum class` które są podobne do standardu C++ `enum class` , ale z uwzględnieniem specyfikator ułatwień dostępu. W obszarze **/CLR**, C ++ 11 `enum class` typ jest dozwolone, ale spowoduje wygenerowanie ostrzeżenia C4472 ma na celu upewnij się, czy na pewno chcesz ISO Typ wyliczeniowy i nie C + +/ CX i C + +/ CLI typu. Aby uzyskać więcej informacji na temat standardu C++ ISO `enum` — słowo kluczowe, zobacz [wyliczenia](../cpp/enumerations-cpp.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Składnia**  
  
```  
  
      access  
      enum class  
      enumeration-identifier  
      [:underlying-type] { enumerator-list } [var];  
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];  
```  
  
 **Parametry**  
  
 *dostęp*  
 Dostępność wyliczenia, które mogą być `public` lub `private`.  
  
 *Identyfikator wyliczenia*  
 Nazwa wyliczenia.  
  
 *Typ podstawowy*  
 (Opcjonalnie) Typ podstawowy wyliczenia.  
  
 (Opcjonalnie. Środowisko wykonawcze systemu Windows tylko) podstawowy typ wyliczenia, które mogą być `bool`, `char`, `char16`, `int16`, `uint16`, `int`, `uint32`, `int64`, lub `uint64`.  
  
 *Moduł wyliczający listy*  
 Rozdzielana przecinkami lista nazw modułu wyliczającego.  
  
 Wartość każdego modułu wyliczającego jest wyrażenie stałej zdefiniowanym albo niejawnie przez kompilator, lub jawnie notacji, *modułu wyliczającego*`=`*wyrażenia*. Domyślnie wartość modułu wyliczającego pierwszy wynosi zero, jeśli został niejawnie zdefiniowany. Wartość każdego kolejnych modułu wyliczającego niejawnie zdefiniowany jest wartością poprzedniego modułu wyliczającego + 1.  
  
 *var*  
 (Opcjonalnie) Nazwa zmiennej typu wyliczenia.  
  
 **Uwagi**  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [wyliczenia](http://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx).  
  
 Należy pamiętać, że kompilator emituje komunikaty o błędach, jeśli wyrażenie stałe, który definiuje wartość modułu wyliczającego nie mogą być reprezentowane przez *typ bazowy*.  Jednak kompilator nie zgłasza błąd dla wartość, która jest nieodpowiedni dla typu bazowego. Na przykład:  
  
-   Jeśli *typ bazowy* jest liczbą i moduł wyliczający określa maksymalną wartość dla tego typu, nie można przedstawić wartości dalej enumeratoin niejawnie zdefiniowany.  
  
-   Jeśli *typ bazowy* jest `bool`, i więcej niż dwa moduły wyliczające niejawnie są zdefiniowane moduły wyliczające po dwóch pierwszych nie może być przedstawiony.  
  
-   Jeśli *typ bazowy* jest `char16`i wartość wyliczenia zakresu od 0xD800 do 0xDFFF, może być reprezentowany wartość. Jednak wartość logicznie niepoprawne, ponieważ reprezentuje ona połowa Unicode dwuskładnikowy i nie powinny być wyświetlane w izolacji.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Składnia**  
  
```  
  
      access  
      enum class  
      name [:type] { enumerator-list } var;  
accessenum structname [:type] { enumerator-list } var;  
```  
  
 **Parametry**  
  
 `access`  
 Dostępność wyliczenia.  Może to być albo **publicznego** lub `private`.  
  
 `enumerator-list`  
 Rozdzielana przecinkami lista identyfikatorów (moduły wyliczające) w wyliczeniu.  
  
 `name`  
 Nazwa wyliczenia.  Nie są dozwolone anonimowe wyliczenia zarządzanych.  
  
 `type`(opcjonalnie)  
 Typ podstawowy elementu *identyfikatory*.  Może to być dowolnego typu skalarne, na przykład podpisem lub bez wersji int, krótka lub długa.  `bool`lub `char` również jest dozwolone.  
  
 `var`(opcjonalnie)  
 Nazwa zmiennej typu wyliczenia.  
  
 **Uwagi**  
  
 **Wylicz klasy** i **enum struct** są równoważne deklaracji.  
  
 Istnieją dwa typy wyliczeń: zarządzane lub C + +/ CX i standard.  
  
 Zarządzane lub C + +/ CX wyliczenia może zdefiniowane w następujący sposób  
  
```cpp  
public enum class day {sun, mon };  
```  
  
 i stanowi odpowiednik semantycznie:  
  
```cpp  
ref class day {  
public:  
   static const int sun = 0;  
   static const int mon = 1;  
};  
```  
  
 Standardowa wyliczenia można zdefiniować w następujący sposób:  
  
```cpp  
enum day2 { sun, mon };  
```  
  
 i stanowi odpowiednik semantycznie:  
  
```cpp  
static const int sun = 0;  
static const int mon = 1;  
```  
  
 Zarządzane nazwy modułu wyliczającego (*identyfikatory*) nie są wstrzykiwane do zakresu, w której zdefiniowano wyliczenia; wszystkie odwołania do wyliczenia musi być w pełni kwalifikowana (*nazwa* `::` *identyfikator*).  Z tego powodu nie można zdefiniować anonimowe wyliczenia zarządzanych.  
  
 Moduły wyliczające standardowe wyliczenia silnie są wstrzykiwane do otaczającego zakresu.  Oznacza to jeśli istnieje inny symbol o tej samej nazwie jako moduł wyliczający w otaczającym zakresie, kompilator wygeneruje błąd.  
  
 W programie Visual C++ 2002 i Visual C++ 2003 moduły wyliczające lekko zostały dodane (widoczne w otaczającym zakresie o ile nie wystąpił inny identyfikator o takiej samej nazwie).  
  
 Jeśli zdefiniowano standardowe wyliczenia C++ (bez **klasy** lub `struct`), kompilowanie z **/CLR** spowoduje wyliczenie ma zostać skompilowana jako zarządzane wyliczenia.  Wyliczenie nadal ma semantykę niezarządzanego wyliczenia.  Uwaga: atrybut injects kompilator `Microsoft::VisualC::NativeEnumAttribute`, która rozpoznaje kompilatora Visual C++, do identyfikowania zamiar programisty dla wyliczenia za natywnym wyliczeniem.  Inne kompilatory po prostu zostanie wyświetlony standardowy wyliczenia jako zarządzane wyliczenia.  
  
 Wyliczenia o nazwie, standard, kompilowanych z/CLR będzie widoczny w zestawu zarządzanego wyliczenia i mogą być używane przez inne zarządzane kompilatora.   Nienazwane wyliczenia standardowy nie będzie jednak widocznego publicznie z zestawu.  
  
 Visual C++ 2002 i program Visual C++ 2003, standard wyliczenia, używany jako typ parametru funkcji:  
  
```cpp  
// mcppv2_enum.cpp  
// compile with: /clr  
enum E { a, b };  
void f(E) {System::Console::WriteLine("hi");}  
  
int main() {  
   E myi = b;  
   f(myi);  
}  
```  
  
 czy emitować następujące opcje w MSIL dla podpisu funkcji:  
  
```  
void f(int32);  
```  
  
 Jednak w bieżącej wersji kompilatora, standardowe enum jest emitowany jako zarządzane wyliczenia [NativeEnumAttribute] i następuje w MSIL dla podpisu funkcji:  
  
```  
void f(E)  
```  
  
 Aby uzyskać więcej informacji na temat natywnych typów wyliczeniowych zobacz [deklaracje modułów Wyliczających języka C++](../cpp/enumerations-cpp.md).  
  
 Aby uzyskać więcej informacji dotyczących wyliczenia CLR zobacz:  
  
-   [Typ podstawowy wyliczenia](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 desc  
  
```cpp  
// mcppv2_enum_2.cpp  
// compile with: /clr  
// managed enum  
public enum class m { a, b };  
  
// standard enum  
public enum n { c, d };  
  
// unnamed, standard enum  
public enum { e, f } o;  
  
int main()   
{  
   // consume managed enum  
   m mym = m::b;  
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);  
   System::Console::WriteLine("convert to int: {0}", (int)mym);  
  
   // consume standard enum  
   n myn = d;  
   System::Console::WriteLine(myn);  
  
   // consume standard, unnamed enum  
   o = f;  
   System::Console::WriteLine(o);  
}   
```  
  
 **Output**  
  
```Output  
no automatic conversion to int: b  
  
convert to int: 1  
  
1  
  
1  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)