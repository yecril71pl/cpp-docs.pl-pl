---
title: '&lt;Lista&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- list
- <list>
dev_langs:
- C++
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac136ac009f9597c3773e210aaabf4adcb6b738
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433253"
---
# <a name="ltlistgt-visual-c"></a>&lt;Lista&gt; (Visual C++)

\<Listheader > Blokuj służy do definiowania wiersz nagłówka tabeli lub definicji listy. Podczas definiowania tabeli, wystarczy podać wpis termin w nagłówku.

## <a name="syntax"></a>Składnia

```
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>Parametry

*Termin*<br/>
Termin, aby zdefiniować, które są definiowane w `description`.

*Opis elementu*<br/>
Element w punktora lub Lista numerowana lub definicji `term`.

## <a name="remarks"></a>Uwagi

Każdy element na liście jest określony za pomocą \<elementu > bloku. Podczas tworzenia listy definicji, musisz podać obydwie wartości `term` i `description`. Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.

Masz tyle listy lub tabeli \<elementu > blokuje zgodnie z potrzebami.

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)