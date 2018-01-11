---
title: '&lt;param&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- param
- <param>
dev_langs: C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf74dc4f0488c3c1b41b8ee55c20610684434ee2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)
\<Param > tag powinny być używane w komentarz dla deklaracji metody opisujący jeden z parametrów metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru metody.  Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `name`.  
  
 `description`  
 Opis parametru.  
  
## <a name="remarks"></a>Uwagi  
 Tekst dla \<param > będą wyświetlane w IntelliSense, [przeglądarki obiektów](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470)i w raporcie Web komentarz kodu.  
  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)