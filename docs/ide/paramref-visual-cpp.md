---
title: '&lt;paramref&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- paramref
- <paramref>
dev_langs: C++
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 591aaaff84fa347e2753e2dc3899bb7f6900a5f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltparamrefgt-visual-c"></a>&lt;paramref&gt; (Visual C++)
\<Paramref > tag udostępnia sposób wskazują, że wyraz jest parametrem. Aby sformatować ten parametr w jakiś sposób różne mogą być przetwarzane pliku XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru do odwoływania się do.  Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `name`.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
  
```  
// xml_paramref_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_paramref_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// The <paramref name="Int1"/> parameter takes a number.  
   /// </summary>  
   void MyMethod(int Int1) {}  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)