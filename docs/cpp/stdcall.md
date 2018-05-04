---
title: __stdcall | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __stdcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f018a87f7a73de6500294b0817263e6f847af8ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="stdcall"></a>__stdcall
**Microsoft Specific**  
  
 `__stdcall` Konwencji wywoływania służy do wywołania funkcji Win32 API. Wywoływany czyści stosu, więc sprawia, że kompilator **vararg** funkcji `__cdecl`. Funkcje programu wykorzystujące Konwencja wywoływania wymagają prototypu funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
return-type __stdcall function-name[(argument-list)]  
```  
  
## <a name="remarks"></a>Uwagi  
 Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.  
  
|Element|Implementacja|  
|-------------|--------------------|  
|Kolejność przekazywania argumentów|Od prawej do lewej.|  
|Przekazywanie argumentów Konwencji|Według wartości chyba że przekazywany jest wskaźnik lub odwołanie do typu.|  
|Odpowiedzialność za utrzymanie stosu|Wywoływana funkcja POP własną argumentów ze stosu.|  
|Konwencja dekorowania nazw|Znaku podkreślenia (_) jest prefiksem nazwy. Nazwa następuje znak @ (@) następuje liczba bajtów (dziesiętna) na liście argumentów. W związku z tym funkcja zadeklarowana jako `int func( int a, double b )` ma przypisany w następujący sposób: `_func@12`|  
|Konwencja translacji wielkości liter|Brak|  
  
 [GZ](../build/reference/gd-gr-gv-gz-calling-convention.md) określa — opcja kompilatora `__stdcall` dla wszystkich funkcji, nie jest jawnie zadeklarowana z różnych konwencję wywołania.  
  
 Zadeklarowane za pomocą funkcji `__stdcall` modyfikator zwracanych wartości taki sam sposób jak zadeklarowane za pomocą funkcji [__cdecl](../cpp/cdecl.md).  
  
 Na ARM i x64 procesorów, `__stdcall` zaakceptowaniu i ignorowane przez kompilator; na ARM i x64 architektur przez Konwencję, argumenty są przekazywane w rejestrach, gdy jest to możliwe, a pozostałe argumenty są przekazywane na stosie.  
  
 W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Podane tej definicji klasy  
  
```cpp  
struct CMyClass {  
   void __stdcall mymethod();  
};  
```  
  
 this  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 jest to równoważne  
  
```cpp  
void __stdcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wykorzystania __**stdcall** powoduje we wszystkich `WINAPI` funkcja typy są traktowane jako wywołanie standardowe:  
  
```cpp  
// Example of the __stdcall keyword  
#define WINAPI __stdcall  
// Example of the __stdcall keyword on function pointer  
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)