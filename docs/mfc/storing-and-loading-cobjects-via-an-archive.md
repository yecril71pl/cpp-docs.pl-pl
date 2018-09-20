---
title: Przechowywanie i ładowanie obiektów CObject za pomocą archiwum | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e19626fab2e44bf88b4a378d094daaf7c377ad5d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436965"
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

