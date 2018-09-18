---
title: '&lt;Uwagi&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- remarks
- <remarks>
dev_langs:
- C++
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bf60222b276050af5296d678985eda8fd12948b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027573"
---
# <a name="ltremarksgt-visual-c"></a>&lt;Uwagi&gt; (Visual C++)
\<Uwagi > tag jest używany do dodawania informacji o typie, informacje uzupełniające określony za pomocą [ \<podsumowania >](../ide/summary-visual-cpp.md). Te informacje są wyświetlane w [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code) i w raporcie Web komentarzy kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parametry  
*Opis elementu*<br/>
Opis elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)