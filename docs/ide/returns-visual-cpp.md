---
title: '&lt;Zwraca&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- returns
- <returns>
dev_langs:
- C++
helpviewer_keywords:
- returns C++ XML tag
- <returns> C++ XML tag
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b9956299370b4a41ce725cf903ff2aefe55bf53
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33336739"
---
# <a name="ltreturnsgt-visual-c"></a>&lt;Zwraca&gt; (Visual C++)
\<Zwraca > tag powinny być używane w komentarz dla deklaracji metody do opisywania wartości zwracanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Opis wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
  
```  
// xml_returns_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_returns_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <returns>Returns zero.</returns>  
   int GetZero() { return 0; }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)