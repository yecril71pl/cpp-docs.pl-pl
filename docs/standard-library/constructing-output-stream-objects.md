---
title: Konstruowanie obiektów strumienia wyjściowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff3c924327c11d00dd9137a91ebd19ef7bdc9eaa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850075"
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
