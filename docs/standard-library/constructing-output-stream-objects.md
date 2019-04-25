---
title: Konstruowanie obiektów strumienia wyjściowego
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: 7da7d9dd0fae3ce3fa21ecd774f88643dca49c26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212004"
---
# <a name="constructing-output-stream-objects"></a>Konstruowanie obiektów strumienia wyjściowego

Jeśli używasz tylko wstępnie zdefiniowanych `cout`, `cerr`, lub `clog` obiektów, nie trzeba utworzyć strumień wyjściowy. Należy użyć konstruktory:

- [Dane wyjściowe pliku Stream konstruktorów](#vclrfoutputfilestreamconstructorsanchor1)

- [Konstruktory Stream ciągu danych wyjściowych](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Dane wyjściowe pliku Stream konstruktorów

Możesz utworzyć strumień wyjściowy plik na jeden z dwóch sposobów:

- Użyj domyślnego konstruktora, a następnie wywołaj `open` funkcja elementu członkowskiego.

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

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Konstruktory Stream ciągu danych wyjściowych

Aby utworzyć strumień wyjściowy ciągu, można użyć `ostringstream` w następujący sposób:

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` "Manipulator" dodaje niezbędne kończącego znaku null na ciąg.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
