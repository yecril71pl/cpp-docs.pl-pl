---
title: static_assert | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: static_assert_cpp
dev_langs: C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9073f513000684fd75ccdba250c2f92513a94bdc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="staticassert"></a>static_assert
Testy potwierdzenia oprogramowania, w czasie kompilacji. Jeśli określone wyrażenie stałe jest `false`, kompilator Wyświetla określony komunikat, jeśli zostało ono określone i kompilacja zakończy się niepowodzeniem z powodu błędu C2338; w przeciwnym razie deklaracji nie ma wpływu.  
  
## <a name="syntax"></a>Składnia  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`constant-expression`|Całkowite stałe wyrażenie, które mogą być konwertowane na wartość logiczną.<br /><br /> Jeśli obliczane wyrażenie jest równy zero (false), `string-literal` parametru jest wyświetlana i kompilacja zakończy się niepowodzeniem z powodu błędu. Jeśli wyrażenie jest różna od zera (true), `static_assert` deklaracji nie ma wpływu.|  
|`string-literal`|Komunikat jest wyświetlany, jeśli `constant-expression` parametru wynosi zero. Komunikat jest ciąg znaków w [podstawowy zestaw znaków](../c-language/ascii-character-set.md) kompilatora; jest, a nie [znaki wielobajtowe i dwubajtowe](../c-language/multibyte-and-wide-characters.md).|  
  
## <a name="remarks"></a>Uwagi  
 `constant-expression` Parametr `static_assert` reprezentuje deklaracji *potwierdzenia oprogramowania*. Potwierdzenie oprogramowania określa warunek, który będzie mieć wartość true w określonym punkcie w programie. Jeśli warunek jest spełniony, `static_assert` deklaracji nie ma wpływu. Jeśli warunek nie jest spełniony, potwierdzenie nie powiedzie się, kompilator wyświetla komunikat w `string-literal` parametr i niepowodzenia kompilacji z powodu błędu. W programie Visual Studio 2017 i nowszych parametr literał ciągu jest opcjonalny. 
  
 `static_assert` Deklaracji testów potwierdzenia oprogramowania, w czasie kompilacji. Z kolei [assert — makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro potwierdzenia oprogramowania, w czasie wykonywania testów i wiąże się z kosztami czasie wykonywania w przestrzeni lub w czasie. `static_assert` Deklaracja jest szczególnie przydatna w przypadku debugowania szablonów, ponieważ argumenty szablonu może być uwzględniony w `constant-expression` parametru.  
  
 Kompilator sprawdza `static_assert` deklaracji pod kątem błędów składni w przypadku zgłoszenia. Oblicza kompilator `constant-expression` parametru natychmiast, jeśli nie jest zależny od parametru szablonu. W przeciwnym razie kompilator ocenia `constant-expression` parametru podczas tworzenia wystąpienia klasy szablonu. W związku z tym, kompilator może wystawiać komunikatów diagnostycznych raz po napotkaniu deklaracji i ponownie, jeśli szablon zostanie uruchomiony.  
  
 Można użyć `static_assert` — słowo kluczowe w przestrzeni nazw, klasy lub zakres bloku. ( `static_assert` — Słowo kluczowe jest technicznie deklaracji, nawet jeśli nie wprowadzać nową nazwę do programu, ponieważ mogą być używane w zakresie przestrzeni nazw.)  
  
## <a name="description"></a>Opis  
 W poniższym przykładzie `static_assert` deklaracja zawiera zakresie przestrzeni nazw. Ponieważ kompilator zna rozmiar typu `void *`, natychmiast obliczone wyrażenie.  
  
## <a name="example"></a>Przykład  
  
```  
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>Opis  
 W poniższym przykładzie `static_assert` deklaracja zawiera zakres klasy. `static_assert` Weryfikuje, czy parametr szablonu *zwykły stare dane* typ (POD). Kompilator sprawdza `static_assert` deklaracji jest zadeklarowana, ale nie może oszacować `constant-expression` parametru do `basic_string` w tworzeniu wystąpienia szablonu klasy `main()`.  
  
## <a name="example"></a>Przykład  
  
```  
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
 W poniższym przykładzie `static_assert` deklaracja o zakresie bloku. `static_assert` Sprawdza, czy rozmiar struktury VMPage jest równa pagesize wirtualnej pamięci systemu.  
  
## <a name="example"></a>Przykład  
  
```  
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
 [Assert — makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [Szablony](../cpp/templates-cpp.md)   
 [Zestaw znaków ASCII](../c-language/ascii-character-set.md)   
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)