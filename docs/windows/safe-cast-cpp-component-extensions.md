---
title: safe_cast (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c889d39df4d900beba5c9b41015e62293fdbbcde
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891519"
---
# <a name="safecast-c-component-extensions"></a>safe_cast (C++ Component Extensions)
`safe_cast` Operacji zwraca określone wyrażenie jako określony typ, w przypadku powodzenia; w przeciwnym razie zwraca `InvalidCastException`.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych.)  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 `safe_cast` Umożliwia zmianę typu określone wyrażenie. W sytuacjach, w pełni nieoczekiwany zmienna lub parametr być możliwa do przekonwertowania dla określonego typu można użyć polecenia safe_cast bez bloku try-catch do wykrywania programowania błędów podczas tworzenia. Aby uzyskać więcej informacji, zobacz [rzutowanie (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx).  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator typu*  
 Typ docelowy konwersji *wyrażenie* do. Dojście do odwołanie lub typ wartości, typu wartości lub odwołanie śledzące do typu odwołanie lub wartość.  
  
 *wyrażenie*  
 Wyrażenie obliczane do dojścia do odwołanie lub typ wartości, typu wartości lub odwołanie śledzące do typu odwołanie lub wartość.  
  
### <a name="remarks"></a>Uwagi  
 `safe_cast` zgłasza wyjątek `InvalidCastException` Jeśli go nie można przekonwertować *wyrażenie* na typ określony przez *identyfikator typu*. Aby przechwycić `InvalidCastException`, określ [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md) — opcja kompilatora i użyj instrukcji try/catch.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje sposób użycia `safe_cast` ze środowiska uruchomieniowego systemu Windows.  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **Output**  
  
```Output  
Caught expected exception: InvalidCastException  
```  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 `safe_cast` Umożliwia Zmień typ wyrażenia i generowanie kodu MSIL możliwe do zweryfikowania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator typu*  
 Dojście do odwołanie lub typ wartości, typu wartości lub odwołanie śledzące do typu odwołanie lub wartość.  
  
 *wyrażenie*  
 Wyrażenie obliczane do dojścia do odwołanie lub typ wartości, typu wartości lub odwołanie śledzące do typu odwołanie lub wartość.  
  
### <a name="remarks"></a>Uwagi  
 Wyrażenie `safe_cast<` *identyfikator typu*`>(`*wyrażenie* `)` Konwertuje wyrażenia argumentu operacji do obiektu typu typu-ID.  
  
 Kompilator będzie akceptować [static_cast](../cpp/static-cast-operator.md) w większości miejsc, w których akceptował `safe_cast`.  Jednak `safe_cast` może utworzyć zweryfikowania MSIL, gdzie jako `static_cast` może utworzyć MSIL niemożliwy.  Zobacz [czystej i weryfikowalny kod (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) i [Peverify.exe (narzędzie PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) Aby uzyskać więcej informacji na temat weryfikowalny kod.  
  
 Podobnie jak `static_cast`, `safe_cast` wywołuje konwersje zdefiniowane przez użytkownika.  
  
 Aby uzyskać więcej informacji na temat rzutowania zobacz [operatory rzutowania](../cpp/casting-operators.md).  
  
 `safe_cast` nie ma zastosowania **const_cast** (rzutowania z usuwaniem **const**).  
  
 `safe_cast` znajduje się w przestrzeni nazw cli.  Zobacz [platformy, domyślna i cli przestrzenie nazw](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji na temat **safe_cas**t, zobacz:  
  
-   [Rzutowania w stylu języka C z/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [Instrukcje: korzystanie z polecenia safe_cast w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Jeden przykład którym kompilator nie będzie akceptować `static_cast` , ale będzie akceptować `safe_cast` dotyczy rzutowania między typami niepowiązanych interfejsu.  Z `safe_cast`, kompilator nie będzie wystawiać błąd konwersji i wykona sprawdzenie w czasie wykonywania, czy możliwe jest rzutowania  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **Output**  
  
```Output  
Caught expected exception  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)