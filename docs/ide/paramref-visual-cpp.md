---
title: '&lt;paramref&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- paramref
- <paramref>
dev_langs:
- C++
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a63caea7186114244927b9ede4c63ed97871d6e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111267"
---
# <a name="ltparamrefgt-visual-c"></a>&lt;paramref&gt; (Visual C++)
\<Paramref > tag zapewnia sposób, aby wskazać, że wyraz jest parametrem. Plik XML mogą być przetwarzane do formatowania tego parametru w jakiś sposób distinct.  
  
## <a name="syntax"></a>Składnia  
  
```  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
*Nazwa*<br/>
Nazwa parametru do odwoływania się do.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `name`.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
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