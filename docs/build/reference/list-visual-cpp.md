---
title: '&lt;Lista > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: fd5b97ac518bc4075697da7b6ed88ed46bdd8814
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823882"
---
# <a name="ltlistgt"></a>&lt;list&gt;

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

*description*<br/>
Element w punktora lub Lista numerowana lub definicji `term`.

## <a name="remarks"></a>Uwagi

Każdy element na liście jest określony za pomocą \<elementu > bloku. Podczas tworzenia listy definicji, musisz podać obydwie wartości `term` i `description`. Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.

Masz tyle listy lub tabeli \<elementu > blokuje zgodnie z potrzebami.

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

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

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
