---
title: '&lt;Lista> (Komentarze w dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- list
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: 24f9b17c67b8f951743fd51c04266b05dad235c7
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041968"
---
# <a name="ltlistgt-and-ltlistheadergt"></a>&lt;List &gt; i &lt; listheader&gt;

\<listheader>Blok służy do definiowania wiersza nagłówka tabeli lub listy definicji. Podczas definiowania tabeli należy podać tylko wpis dla terminu w nagłówku.

## <a name="syntax"></a>Składnia

```xml
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

*mandat*<br/>
Termin do zdefiniowania, który zostanie zdefiniowany w `description` .

*zharmonizowan*<br/>
Element na liście punktowanej lub numerowanej lub definicji `term` .

## <a name="remarks"></a>Uwagi

Każdy element na liście jest określony za pomocą \<item> bloku. Podczas tworzenia listy definicji należy określić zarówno, `term` jak i `description` . Jednak dla tabeli, listy punktowanej lub listy numerowanej wystarczy podać wpis dla `description` .

Lista lub tabela może zawierać tyle \<item> bloków, ile jest to konieczne.

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

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
