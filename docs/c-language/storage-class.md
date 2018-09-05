---
title: Klasa magazynu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5473a3c11268e7e8563d95392ec6439e55c03bf4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757165"
---
# <a name="storage-class"></a>Klasa magazynu
Specyfikator klasy magazynu w definicji funkcji daje funkcji `extern` lub **statyczne** klasy magazynowania.  
  
## <a name="syntax"></a>Składnia

*Definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> *atrybutu seq*<sub>zoptymalizowany pod kątem</sub> *deklaratora* *lista deklaracji*  <sub>zoptymalizowany pod kątem</sub> *compound-statement*

/\* *Atrybut seq* jest Specific dla Microsoft \*/

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>  

*Storage-class-specifier*: /\* dla definicji funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statyczne**

Jeśli definicja funkcji nie obejmuje *storage-class-specifier*, domyślna klasa magazynu `extern`. Można jawnie zadeklarować funkcję jako `extern`, ale nie jest to wymagane.  
  
Jeśli deklaracja funkcji zawiera *storage-class-specifier* `extern`, identyfikator ma te same powiązania co dowolna widoczna deklaracja identyfikatora z zakresem pliku. Jeśli nie ma żadnej widocznej deklaracji z zakresem pliku, identyfikator ma powiązania zewnętrzne. Jeśli identyfikator ma zakres pliku a nie *storage-class-specifier*, identyfikator ma powiązania zewnętrzne. Powiązania zewnętrzne oznaczają, że każde wystąpienie identyfikatora oznacza ten sam obiekt lub funkcję. Zobacz [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md) uzyskać więcej informacji dotyczących powiązań i zakresu pliku.  
  
Deklaracje funkcji o zakresie bloku ze specyfikatorem klasy magazynu innym niż `extern`.  
  
Funkcja z **statyczne** klasę magazynu jest widoczna tylko w pliku źródłowym, w którym jest zdefiniowany. Wszystkie inne funkcje, niezależnie od tego, czy posiadają klasę magazynu `extern` jawnie lub niejawnie, są widoczne we wszystkich plikach z kodem źródłowym w programie. Jeśli **statyczne** pożądana jest klasa magazynu, musi być zadeklarowana podczas pierwszego wystąpienia deklaracji funkcji (jeśli istnieje), a w definicji funkcji.  
  
**Microsoft Specific**  
  
Po włączeniu rozszerzeń Microsoft funkcja pierwotnie zadeklarowana bez klasy magazynu (lub za pomocą `extern` klasy magazynowania) otrzymuje **statyczne** klasy magazynu, jeśli definicja funkcji znajduje się w tym samym pliku źródłowym i Definicja jawnie określa **statyczne** klasy magazynowania.  
  
Podczas kompilacji z opcją kompilatora /Ze, funkcje zadeklarowane wewnątrz bloku za pomocą słowa kluczowego `extern` mają globalną widoczność. Nie ma to zastosowania podczas kompilowania z opcją /Za. Na tej funkcji nie można polegać, jeżeli trzeba uwzględnić przenośność kodu źródłowego.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
[Definicje funkcji języka C](../c-language/c-function-definitions.md)