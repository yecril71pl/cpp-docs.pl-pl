---
title: '&lt;param&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69e2950fcc0b29fb819445f3216ef262a2657e4a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686424"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)
\<Param > używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru metody.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `name`.  
  
 `description`  
 Opis parametru.  
  
## <a name="remarks"></a>Uwagi  
 Tekst dla \<param > będą wyświetlane w technologii IntelliSense, [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code)i w raporcie Web komentarzy kodu.  
  
 Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
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