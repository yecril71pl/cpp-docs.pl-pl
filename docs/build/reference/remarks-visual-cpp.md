---
title: '&lt;uwagi > (C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 096280526b12feff33377a705f7c03548a1f0f13
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988651"
---
# <a name="ltremarksgt"></a>&lt;uwagi&gt;

Tag \<uwagi > służy do dodawania informacji o typie, uzupełnienie informacji określonych za pomocą [\<podsumowania >](summary-visual-cpp.md). Te informacje są wyświetlane w [Przeglądarka obiektów](/visualstudio/ide/viewing-the-structure-of-code) i w raporcie w sieci Web komentarza do kodu.

## <a name="syntax"></a>Składnia

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>Parametry

*zharmonizowan*<br/>
Opis elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```cpp
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
