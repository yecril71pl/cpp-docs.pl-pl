---
title: '&lt;Remarks > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 0d0c63d55de80f498498a6873dacb5e83fc956b7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823771"
---
# <a name="ltremarksgt"></a>&lt;Uwagi&gt;

\<Uwagi > tag jest używany do dodawania informacji o typie, informacje uzupełniające określony za pomocą [ \<podsumowania >](summary-visual-cpp.md). Te informacje są wyświetlane w [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code) i w raporcie Web komentarzy kodu.

## <a name="syntax"></a>Składnia

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Opis elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
