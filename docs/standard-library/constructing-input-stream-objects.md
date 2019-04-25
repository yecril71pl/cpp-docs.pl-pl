---
title: Konstruowanie obiektów strumienia danych wejściowych
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: 89d681f1a092957bc966d2ec788a0f9aa2261ada
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62211991"
---
# <a name="constructing-input-stream-objects"></a>Konstruowanie obiektów strumienia danych wejściowych

Jeśli używasz tylko `cin` obiektu, nie trzeba utworzyć strumień wejściowy. Jeśli używasz, musi utworzyć strumień wejściowy:

- [Konstruktory Stream pliku wejściowego](#vclrfinputfilestreamconstructorsanchor8)

- [Ciąg wejściowy Stream konstruktorów](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a> Konstruktory Stream pliku wejściowego

Istnieją dwa sposoby tworzenia strumienia pliku wejściowego:

- Użyj **void** argument konstruktora, następnie wywołać `open` funkcja elementu członkowskiego:

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- Określ flagi nazwę pliku i tryb w wywołaniu konstruktora, w ten sposób otwierania pliku w procesie tworzenia:

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="vclrfinputstringstreamconstructorsanchor9"></a> Ciąg wejściowy Stream konstruktorów

Ciąg wejściowy strumień konstruktory wymagają adres przydzielony wstępnie preinitialized magazynu:

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
