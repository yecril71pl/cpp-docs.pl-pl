---
title: Przechowywanie i ładowanie obiektów CObject za pomocą archiwum
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: 370e8202d1bd1cda04edbdbd12bd936bdf5ef7b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493694"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Przechowywanie i ładowanie obiektów CObject za pomocą archiwum

Przechowywanie i ładowanie `CObject`s za pomocą archiwum wymaga dodatkowego rozważenia. W niektórych przypadkach należy wywołać `Serialize` funkcji obiektu, którym `CArchive` obiektu jest parametrem `Serialize` wywołanie, a nie za pomocą **< \<** lub **>>** operatora `CArchive`. Jest to ważne fakt, o których należy pamiętać, że `CArchive` **>>** konstrukcji operator `CObject` w pamięci na podstawie `CRuntimeClass` informacji wcześniej zapisane w pliku przez zapisywanie archiwum.

W związku z tym, czy używać `CArchive` **< \<** i **>>** operatorów w porównaniu z wywołaniem `Serialize`, zależy od tego, czy możesz *muszą* archiwum ładowania dynamicznie odtworzenie obiektu na podstawie zapisanych wcześniej `CRuntimeClass` informacji. Użyj `Serialize` funkcji w następujących przypadkach:

- Podczas deserializacji obiektu, znasz dokładną klasy obiektu wcześniej.

- Podczas deserializacji obiektu, masz już pamięci przydzielonej dla niego.

> [!CAUTION]
>  Jeśli załadujesz obiekt przy użyciu `Serialize` funkcji, należy również zapisać obiekt przy użyciu `Serialize` funkcji. Nie należy przechowywać przy użyciu `CArchive` **<<** operatora i następnie obciążenia za pomocą polecenia `Serialize` funkcji lub przechowywane za pomocą `Serialize` działać, a następnie załadować przy użyciu `CArchive >>` operatora.

W poniższym przykładzie pokazano przypadki:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

Podsumowując, jeśli klasa serializacji definiuje osadzone `CObject` jako członka, wykonaj następujące czynności *nie* użyj `CArchive` **< \<** i **>>** operatory dla tego obiektu, ale powinien wywoływać `Serialize` zamiast tego funkcji. Ponadto jeśli klasa serializacji definiuje wskaźnik do `CObject` (lub obiekt pochodzący od `CObject`) jako członka, ale konstrukcje ten inny obiekt w jego własnej konstruktora, należy także wywołać `Serialize`.

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)

