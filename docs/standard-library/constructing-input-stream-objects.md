---
title: "Konstruowanie obiektów strumienia wejściowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a189fa948bc8c6be7acdac0dcc50e9585e82a082
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="constructing-input-stream-objects"></a>Konstruowanie obiektów strumienia danych wejściowych
Jeśli używasz tylko `cin` obiektu, nie trzeba utworzyć strumienia wejściowego. Strumień wejściowy musi utworzyć, korzystając z:  
  
- [Konstruktory strumienia wejściowego](#vclrfinputfilestreamconstructorsanchor8)  
  
- [Ciąg wejściowy strumienia konstruktorów](#vclrfinputstringstreamconstructorsanchor9)  
  
##  <a name="vclrfinputfilestreamconstructorsanchor8">Konstruktory strumienia wejściowego</a>  
 Istnieją dwa sposoby tworzenia strumienia pliku wejściowego:  
  
-   Użyj `void` konstruktora argumentów wywoływać `open` funkcji członkowskiej:  
  
 ```  
    ifstream myFile; // On the stack  
    myFile.open("filename");

 
    ifstream* pmyFile = new ifstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   Określ flagi nazwę pliku i tryb w wywołaniu konstruktora, w ten sposób otwierania pliku podczas procesu tworzenia:  
  
 ```  
    ifstream myFile("filename");
```  
  
##  <a name="vclrfinputstringstreamconstructorsanchor9">Ciąg wejściowy strumienia konstruktorów</a>  
 Ciąg wejściowy strumienia konstruktorów wymagają adresu przydzielony wstępnie, wstępnie zainicjowanych magazynu:  
  
```  
string s("123.45");

double amt;  
istringstream myString(s);

//istringstream myString("123.45") also works  
myString>> amt; // amt contains 123.45  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wejściowe](../standard-library/input-streams.md)

