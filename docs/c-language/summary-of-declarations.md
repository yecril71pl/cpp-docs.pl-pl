---
title: Podsumowanie deklaracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a391ee0ee21925c59e5a95cb060f9897b3ef223c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214869"
---
# <a name="summary-of-declarations"></a>Podsumowanie deklaracji

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *atrybutu seq*<sub>zoptymalizowany pod kątem</sub> *init-declarator-list*<sub>zoptymalizowany pod kątem</sub> **;**

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>

*Atrybut seq* :&nbsp; &nbsp; &nbsp; &nbsp; / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atrybut* *atrybutu seq*<sub>zoptymalizowany pod kątem</sub>

*atrybut* : jeden z&nbsp; &nbsp; &nbsp; &nbsp; / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list***,***init-declarator* 

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator***=***inicjatora*  / \* inicjowania skalarne     \*/

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Automatycznie**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Zarejestruj się**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statyczne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Element TypeDef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl modyfikator seq* **)**  / \* Specific firmy Microsoft \*/

*Specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Krótka**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**długi**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Podwójne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Podpisany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Bez znaku**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator struktury lub Unii*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu wyliczeniowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Nazwa TypeDef*

*Kwalifikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Volatile**

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*deklarator bezpośrednio*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklaratora* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **[** *wyrażenie_stałe*<sub>zoptymalizowany pod kątem</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy parametrów typu* **)**  / \* deklaratora nowy styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**  / \* Obsolete stylu deklarator \*/

*wskaźnik*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub> *wskaźnika*

*listy parametrów typu*:&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; / \* Lista parametrów \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,...**

*Lista parametrów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,** *deklaracji parametru*

*Lista typów kwalifikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista typów kwalifikator* *kwalifikator typu*

*Specyfikator typu wyliczeniowego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wyliczenie** *identyfikator*<sub>zoptymalizowany pod kątem</sub> **{** *lista_modułów_wyliczających* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wyliczenie** *identyfikator*

*Moduł wyliczający listę*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Moduł wyliczający*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Moduł wyliczający listę* **,** *modułu wyliczającego*

*Moduł wyliczający*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia* **=** *wyrażenia stałego*

*Stała wyliczenia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator struktury lub Unii*<sub>zoptymalizowany pod kątem</sub> **{** *struktury deklaracji listy* **}** *struktury lub Unii Identyfikator*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**— Struktura**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Unia**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja — struktura*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura deklaracji listy* *deklaracji struktury*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator kwalifikator listy* *struktury declarator-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura declarator* *struktury declarator-list* **,** *deklaratora — struktura*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *deklaratora*<sub>zoptymalizowany pod kątem</sub> **:** *wyrażenia stałego*

*Deklaracja parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *deklaratora*  / \* deklaratora nazwane \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub>  / \* deklaratora anonimowe \*/

*Lista identyfikatorów*: /\* dla deklaratora w starym stylu \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista identyfikatorów* **,** *identyfikator*

*deklarator abstrakcyjny*: /\* używane z deklaratorów anonimowe \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wskaźnik*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *bezpośrednio abstrakcyjny declarator*

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *abstrakcyjny declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezpośrednie abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub> **[** *wyrażenie_stałe*<sub>zoptymalizowany pod kątem</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezpośrednie abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub> **(** *listy parametrów typu*<sub>zoptymalizowany pod kątem</sub> **)**

*Inicjator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia przypisania*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *listy inicjatorów* **}**  / \* dla inicjowania agregacji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *listy inicjatorów* **,}**

*initializer-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inicjator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*listy inicjatorów* **,** *inicjatora*

*Nazwa typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator kwalifikator listy* *abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub>

*Nazwa TypeDef*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*rozszerzony decl modyfikator seq*:&nbsp; &nbsp; &nbsp; &nbsp; / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl modyfikator*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony decl modyfikator seq* *extended-decl — modyfikator*

*rozszerzony decl modyfikator*:&nbsp; &nbsp; &nbsp; &nbsp; / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wątek**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"naked"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)<br/>
[Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)<br/>
[Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)