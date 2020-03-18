---
title: '> listy &lt;(C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- list
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: 102cf9f7b1b867a012f662ce786d97012826abd1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439301"
---
# <a name="ltlistgt"></a>&lt;list&gt;

Blok \<listheader > służy do definiowania wiersza nagłówka tabeli lub listy definicji. Podczas definiowania tabeli należy podać tylko wpis dla terminu w nagłówku.

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

*mandat*<br/>
Termin do zdefiniowania, który zostanie zdefiniowany w `description`.

*zharmonizowan*<br/>
Element na liście punktowanej lub numerowanej lub definicji `term`.

## <a name="remarks"></a>Uwagi

Każdy element na liście jest określany za pomocą bloku \<elementu >. Podczas tworzenia listy definicji należy określić zarówno `term`, jak i `description`. Jednak dla tabeli, listy punktowanej lub listy numerowanej należy podać tylko wpis dla `description`.

Lista lub tabela może zawierać tyle \<elementów > bloków, zgodnie z potrzebami.

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

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](xml-documentation-visual-cpp.md)
