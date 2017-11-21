---
title: "Konstruowanie obiektów strumienia wyjściowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9bf3e35c311f5e1e270a6fd46d9cfa24b2e4ba4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="constructing-output-stream-objects"></a>Konstruowanie obiektów strumienia wyjściowego
Jeśli używasz tylko wstępnie zdefiniowanych `cout`, `cerr`, lub `clog` obiektów, nie trzeba utworzyć strumienia wyjściowego. Należy użyć konstruktory:  
  
- [Konstruktory strumienia pliku danych wyjściowych](#vclrfoutputfilestreamconstructorsanchor1)  
  
- [Konstruktory strumień ciągu wyjściowego](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a>Konstruktory strumienia pliku danych wyjściowych  
 Można utworzyć strumienia pliku danych wyjściowych w jeden z dwóch sposobów:  
  
-   Przy użyciu domyślnego konstruktora, a następnie wywołać `open` funkcję elementu członkowskiego.  
  
 ```  
    ofstream myFile; // Static or on the stack  
    myFile.open("filename");

 
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   Określ flagi nazwę pliku i tryb w wywołaniu konstruktora.  
  
 ```  
    ofstream myFile("filename", ios_base::out);
```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a>Konstruktory strumień ciągu wyjściowego  
 Aby utworzyć strumienia ciągu wyjściowego, można użyć `ostringstream` w następujący sposób:  
  
```  
    using namespace std;  
string sp;  
ostringstream myString;  
myString <<"this is a test" <<ends;  
sp = myString.str();
// Obtain string  
cout <<sp <endl;   
```  
  
 `ends` "Manipulatora" dodaje znak końcowy null niezbędne do ciągu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wyjściowe](../standard-library/output-streams.md)

