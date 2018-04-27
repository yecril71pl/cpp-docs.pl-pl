---
title: Konstruowanie obiektów strumienia wyjściowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: debc39987efffe149b8b7834ba5416027acadf4e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="constructing-output-stream-objects"></a>Konstruowanie obiektów strumienia wyjściowego

Jeśli używasz tylko wstępnie zdefiniowanych `cout`, `cerr`, lub `clog` obiektów, nie trzeba utworzyć strumienia wyjściowego. Należy użyć konstruktory:

- [Konstruktory strumienia pliku danych wyjściowych](#vclrfoutputfilestreamconstructorsanchor1)

- [Konstruktory strumień ciągu wyjściowego](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Konstruktory strumienia pliku danych wyjściowych

Można utworzyć strumienia pliku danych wyjściowych w jeden z dwóch sposobów:

- Przy użyciu domyślnego konstruktora, a następnie wywołać `open` funkcję elementu członkowskiego.

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- Określ flagi nazwę pliku i tryb w wywołaniu konstruktora.

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Konstruktory strumień ciągu wyjściowego

Aby utworzyć strumienia ciągu wyjściowego, można użyć `ostringstream` w następujący sposób:

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` "Manipulatora" dodaje znak końcowy null niezbędne do ciągu.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
