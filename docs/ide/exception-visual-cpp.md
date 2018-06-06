---
title: '&lt;wyjątek&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- exception
- <exception>
dev_langs:
- C++
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d3d5b7a89a3725ae9dee2065bcd21d8f114ca00
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33323943"
---
# <a name="ltexceptiongt-visual-c"></a>&lt;wyjątek&gt; (Visual C++)
\<Wyjątku > należy określić, które wyjątki może zostać wygenerowany. Ten tag jest stosowany do definicji metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji. Przy użyciu nazwy wyszukiwania reguł, kompilator sprawdza, czy dany wyjątek istnieje i wykonuje translację `member` nazwę kanoniczną element wyjściowy element XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.  
  
 Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  
  
 Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../ide/see-visual-cpp.md).  
  
 `description`  
 Opis.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
 Kompilator Visual C++ podejmie próbę rozpoznawania odwołań cref w jednym przebiegu za pośrednictwem komentarzy do dokumentacji.  W związku z tym jeśli przy użyciu reguł wyszukiwania C++, symbol nie znaleziono przez kompilator, odwołanie zostanie oznaczona jako nierozwiązane. Zobacz [ \<seealso >](../ide/seealso-visual-cpp.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
  
```  
// xml_exception_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_exception_tag.dll  
using namespace System;  
  
/// Text for class EClass.  
public ref class EClass : public Exception {  
   // class definition ...  
};  
  
/// <exception cref="System.Exception">Thrown when... .</exception>  
public ref class TestClass {  
   void Test() {  
      try {  
      }  
      catch(EClass^) {  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)