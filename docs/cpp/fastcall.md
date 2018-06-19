---
title: __fastcall | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fastcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03f286f21f213f5b2a193ccb824ba22b7c7c1f00
ms.sourcegitcommit: 39585672df8874fb5df4e70de97cd7f328fe9880
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2018
ms.locfileid: "34153122"
---
# <a name="fastcall"></a>__fastcall
**Microsoft Specific**  
  
 `__fastcall` Konwencji wywoływania Określa, że argumenty funkcji są przekazywane w rejestrach, gdy jest to możliwe. Konwencja wywoływania dotyczy tylko x86 architektury. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.  
  
|Element|Implementacja|  
|-------------|--------------------|  
|Kolejność przekazywania argumentów|Pierwsze dwie DWORD lub mniejsze argumenty, które znajdują się na liście argumentów od lewej do prawej są przekazywane w rejestrach ECX i EDX; wszystkie inne argumenty nie są przekazywane na stosie od prawej do lewej.|  
|Odpowiedzialność za utrzymanie stosu|Wywoływana funkcja POP argumenty ze stosu.|  
|Konwencja dekorowania nazw|Znak (\@) jest prefiksem nazwy; znak następuje liczba bajtów (dziesiętna) w parametrze listy jest sufiks nazwy.|  
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywana.|  
  
> [!NOTE]
>  Kompilator w przyszłych wersjach może używać różnych rejestrów do przechowywania parametrów.  
  
 Przy użyciu [GR](../build/reference/gd-gr-gv-gz-calling-convention.md) — opcja kompilatora powoduje poszczególnych funkcji w module skompilować jako `__fastcall` chyba, że funkcja zadeklarowano przy użyciu atrybutu powodujące konflikt albo nazwa funkcji jest `main`.  
  
 `__fastcall` — Słowo kluczowe i akceptowany jest ignorowana przez kompilatorów, które odnoszą się do ARM i x64 architektury; na x64 mikroukładu, zwyczajowo pierwsze cztery argumenty są przekazywane w rejestrach, gdy jest to możliwe, a dodatkowe argumenty są przekazywane na stosie. Aby uzyskać więcej informacji, zobacz [omówienie x64 konwencji wywoływania](../build/overview-of-x64-calling-conventions.md). W układzie ARM maksymalnie cztery liczby całkowitej argumentów i osiem argumenty zmiennoprzecinkowe mogą być przekazywane w rejestrach, a dodatkowe argumenty są przekazywane na stosie.  
  
 W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Biorąc pod uwagę tę definicję klasy:  
  
```cpp  
struct CMyClass {  
   void __fastcall mymethod();  
};  
```  
  
 to:  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 jest równoważne temu:  
  
```cpp  
void __fastcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie funkcja `DeleteAggrWrapper` jest przekazywany argumenty w rejestrach:  
  
```cpp  
// Example of the __fastcall keyword  
#define FASTCALL    __fastcall  
  
void FASTCALL DeleteAggrWrapper(void* pWrapper);  
// Example of the __ fastcall keyword on function pointer  
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)
