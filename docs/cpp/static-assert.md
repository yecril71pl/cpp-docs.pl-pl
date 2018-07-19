---
title: static_assert | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_assert_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc51fab2dade4c6bed0456dd353258df82722de5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947947"
---
# <a name="staticassert"></a>static_assert
Testuje asercję oprogramowania w czasie kompilacji. Jeśli podane wyrażenie stałe ma wartość FALSE, kompilator Wyświetla określony komunikat, jeśli zostało ono określone, a kompilacja kończy się niepowodzeniem ze zgłoszeniem błędu C2338; w przeciwnym razie deklaracja nie ma znaczenia.  
  
## <a name="syntax"></a>Składnia  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`constant-expression`|Wyrażenie stałe liczby całkowitej, można przekonwertować na wartość logiczną.<br /><br /> Jeśli obliczane wyrażenie jest równa zero (false), `string-literal` parametru jest wyświetlany, a kompilacja kończy się niepowodzeniem z powodu błędu. Jeśli wyrażenie jest niezerowe (PRAWDA), **static_assert** deklaracja nie ma wpływu.|  
|`string-literal`|Komunikat, który jest wyświetlany, gdy `constant-expression` parametr ma wartość zero. Wiadomość to ciąg znaków w [podstawowy zestaw znaków](../c-language/ascii-character-set.md) z kompilatora; oznacza to, a nie [znaki wielobajtowe ani szerokie](../c-language/multibyte-and-wide-characters.md).|  
  
## <a name="remarks"></a>Uwagi  
 `constant-expression` Parametru **static_assert** reprezentuje deklaracji *asercję oprogramowania*. Potwierdzenie oprogramowania określa warunek, który będzie mieć wartość true w określonym punkcie w programie. Jeśli warunek jest spełniony, **static_assert** deklaracja nie ma wpływu. Jeśli warunek nie jest spełniony, potwierdzenie nie powiedzie się, kompilator wyświetla komunikat w `string-literal` parametr i kompilacja kończy się niepowodzeniem z powodu błędu. W programie Visual Studio 2017 i nowsze parametr literał ciągu jest opcjonalny. 
  
 **Static_assert** deklaracji testuje asercję oprogramowania w czasie kompilacji. Z kolei [assert — makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro testuje asercję oprogramowania w czasie wykonywania i ponosi koszty wykonywania w przestrzeni lub w czasie. **Static_assert** deklaracja jest szczególnie przydatna podczas debugowania szablonów, ponieważ argumenty szablonu mogą być zawarte w `constant-expression` parametru.  
  
 Kompilator sprawdza **static_assert** deklaracji pod kątem błędów składniowych po napotkaniu deklaracji. Kompilator ocenia `constant-expression` parametr natychmiast, jeśli go nie zależy od parametru szablonu. W przeciwnym wypadku kompilator oblicza `constant-expression` parametru podczas tworzenia wystąpienia szablonu. W związku z tym, kompilator może wydać komunikat diagnostyczny raz po napotkaniu deklaracji, a następnie ponownie podczas konkretyzacji szablonu.  
  
 Możesz użyć **static_assert** — słowo kluczowe w przestrzeni nazw, klasy lub zakresie bloku. ( **Static_assert** — słowo kluczowe jest technicznie deklaracją, mimo że nie wprowadza nowej nazwy do tego programu, ponieważ może służyć w zakresie przestrzeni nazw.)  
  
## <a name="description"></a>Opis  
 W poniższym przykładzie **static_assert** deklaracji ma zakres przestrzeni nazw. Ponieważ kompilator zna wybrany rozmiar czcionki `void *`, wyrażenie jest oceniane natychmiast.  
  
## <a name="example"></a>Przykład  
  
```cpp 
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>Opis  
 W poniższym przykładzie **static_assert** deklaracja ma zakres klasy. **Static_assert** sprawdza, czy parametr szablonu jest *zwykłe stare dane* typu (POD). Kompilator sprawdza **static_assert** deklaracji, gdy jest zadeklarowana, ale nie może oszacować `constant-expression` parametru do momentu `basic_string` konkretyzacji szablonu klasy w `main()`.  
  
## <a name="example"></a>Przykład  
  
```cpp 
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(std::is_pod<CharT>::value,  
                  "Template argument CharT must be a POD type in class template basic_string");  
    // ...  
    };  
}  
  
struct NonPOD {  
    NonPOD(const NonPOD &) {}  
    virtual ~NonPOD() {}  
};  
  
int main()  
{  
    std::basic_string<char> bs;  
}  
```  
  
## <a name="description"></a>Opis  
 W poniższym przykładzie **static_assert** deklaracji ma zakres bloku. **Static_assert** sprawdza, czy rozmiar struktury VMPage jest równy pagesize pamięci wirtualnej systemu.  
  
## <a name="example"></a>Przykład  
  
```cpp 
#include <sys/param.h> // defines PAGESIZE  
class VMMClient {  
public:  
    struct VMPage { // ...   
           };  
    int check_pagesize() {  
    static_assert(sizeof(VMPage) == PAGESIZE,  
        "Struct VMPage must be the same size as a system virtual memory page.");  
    // ...  
    }  
// ...  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Potwierdzanie i komunikaty dostarczone przez użytkownika (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [#error — dyrektywa (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [Szablony](../cpp/templates-cpp.md)   
 [Zestaw znaków ASCII](../c-language/ascii-character-set.md)   
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)