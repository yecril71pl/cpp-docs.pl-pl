---
title: __cdecl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __cdecl_cpp
dev_langs:
- C++
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d07c34c11037132b9f9695ec889bb681c7f43951
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414496"
---
# <a name="cdecl"></a>__cdecl
**Microsoft Specific**  
  
 `__cdecl` jest domyślnie Konwencja wywoływania dla programów C i C++. Ponieważ stos jest czyszczona przez obiekt wywołujący, można wykonać **vararg** funkcji. `__cdecl` Konwencji wywoływania tworzy większe pliki wykonywalne niż [__stdcall](../cpp/stdcall.md), ponieważ wymaga ona każde wywołanie funkcji obejmują stosu oczyszczanie kodu. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.  
  
|Element|Implementacja|  
|-------------|--------------------|  
|Kolejność przekazywania argumentów|Od prawej do lewej.|  
|Odpowiedzialność za utrzymanie stosu|Funkcja wywołująca pobiera argumenty ze stosu.|  
|Konwencja dekorowania nazw|Znak podkreślenia (_) jest prefiksem nazwy, chyba że \__cdecl funkcje programu wykorzystujące powiązanie C są eksportowane.|  
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywana.|  
  
> [!NOTE]
>  Aby uzyskać odpowiednie informacje, zobacz [dekorowane nazwy](../build/reference/decorated-names.md).  
  
 Miejsce `__cdecl` modyfikator przed zmiennej lub nazwę funkcji. Ponieważ C nazewnictwa i Konwencje wywoływania są domyślnymi, tylko musisz użyć `__cdecl` w x86 kod jest po określeniu **GV** (vectorcall), **GZ** (stdcall) lub  **GR** — opcja kompilatora (fastcall). [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) wymusza — opcja kompilatora `__cdecl` konwencji wywoływania.  
  
 Na ARM i x64 procesorów, `__cdecl` jest akceptowane, ale zazwyczaj są ignorowane przez kompilator. Przez konwencję na ARM i x64, argumenty są przekazywane w rejestrach, jeżeli jest to możliwe, a pozostałe argumenty są przekazywane na stosie. W x64 kodu, użyj `__cdecl` do przesłonięcia **GV** — opcja kompilatora i użyj x64 niedomyślną konwencję wywołania.  
  
 W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Biorąc pod uwagę tę definicję klasy:  
  
```cpp  
struct CMyClass {  
   void __cdecl mymethod();  
};  
```  
  
 to:  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 jest równoważne temu:  
  
```cpp  
void __cdecl CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, kompilator jest zalecane jest używanie C nazywania i Konwencje wywoływania `system` funkcji.  
  
```cpp  
// Example of the __cdecl keyword on function  
int __cdecl system(const char *);  
// Example of the __cdecl keyword on function pointer  
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)