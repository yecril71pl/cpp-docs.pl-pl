---
title: '&lt;Uwagi&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- remarks
- <remarks>
dev_langs: C++
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 369a8b7a2addaf2fcc39b598b7ce6582c26e1e98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltremarksgt-visual-c"></a>&lt;Uwagi&gt; (Visual C++)
\<Uwagi > tagu umożliwia dodawanie informacji o typie, informacje uzupełniające określono [ \<podsumowania >](../ide/summary-visual-cpp.md). Te informacje są wyświetlane w [przeglądarki obiektów](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) w komentarz kodu — raport w sieci Web.  
  
## <a name="syntax"></a>Składnia  
  
```  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Opis elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
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
 [Plik dokumentacji XML](../ide/xml-documentation-visual-cpp.md)