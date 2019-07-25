---
title: Konstruowanie obiektów strumienia wyjściowego
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: d7bec211f30986deccc869a879dd5155ea70996b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457283"
---
# <a name="constructing-output-stream-objects"></a>Konstruowanie obiektów strumienia wyjściowego

Jeśli używasz tylko wstępnie zdefiniowanych `cout`, `cerr`lub `clog` obiektów, nie musisz tworzyć strumienia wyjściowego. Należy użyć konstruktorów dla:

- [Konstruktory strumienia plików wyjściowych](#vclrfoutputfilestreamconstructorsanchor1)

- [Konstruktory strumienia ciągów wyjściowych](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a>Konstruktory strumienia plików wyjściowych

Strumień pliku wyjściowego można skonstruować na jeden z dwóch sposobów:

- Użyj konstruktora domyślnego, a następnie Wywołaj `open` funkcję członkowską.

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- Określ nazwę pliku i flagi trybu w wywołaniu konstruktora.

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a>Konstruktory strumienia ciągów wyjściowych

Aby utworzyć strumień ciągu wyjściowego, można użyć `ostringstream` w następujący sposób:

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` "Manipulator" dodaje do ciągu niezbędny kończący znak null.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)
