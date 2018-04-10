---
title: SEKCJE (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ab2f021a53e8ae685891863500feb3873e13e2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sections-cc"></a>SEKCJE (C/C++)
Wprowadza sekcji jednego lub więcej `definitions` , które są specyfikatory dostępu w sekcjach pliku wyjściowego projektu.  
  
```  
SECTIONS  
definitions  
```  
  
## <a name="remarks"></a>Uwagi  
 Każda definicja musi być w oddzielnym wierszu. `SECTIONS` — Słowo kluczowe może być w tym samym wierszu jako pierwsza definicja lub w poprzednim wierszu. Plik .def może zawierać jeden lub więcej `SECTIONS` instrukcje.  
  
 To `SECTIONS` instrukcja Ustawia atrybuty dla co najmniej jednej sekcji w pliku obrazu i może służyć do zastępowania domyślne atrybuty dla każdego typu sekcji.  
  
 Format `definitions` jest:  
  
 `.section_name specifier`  
  
 gdzie `.section_name` jest nazwę sekcji w obrazie programu i `specifier` jest co najmniej jednego z następujących modyfikatorów dostępu:  
  
|Modyfikator|Opis|  
|--------------|-----------------|  
|`EXECUTE`|Sekcja jest pliku wykonywalnego|  
|`READ`|Zezwala na operacje odczytu danych|  
|`SHARED`|Udostępnia sekcji między wszystkie procesy, które ładują obrazu|  
|`WRITE`|Zezwala na wykonywanie operacji zapisu na danych|  
  
 Rozdziel nazwy specyfikator się spacją. Na przykład:  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS`oznacza początek listy sekcji `definitions`. Każdy `definition` musi być w oddzielnym wierszu. `SECTIONS` — Słowo kluczowe może być w tym samym wierszu co pierwszy `definition` lub w poprzednim wierszu. Plik .def może zawierać jeden lub więcej `SECTIONS` instrukcje. `SEGMENTS` — Słowo kluczowe jest obsługiwany jako synonimem `SECTIONS`.  
  
 Obsługuje starsze wersje programu Visual C++:  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 `CLASS` — Słowo kluczowe jest obsługiwana w przypadku zgodności, ale został zignorowany.  
  
 Sposób, aby określić atrybuty sekcji równoważny jest z [/SECTION](../../build/reference/section-specify-section-attributes.md) opcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)