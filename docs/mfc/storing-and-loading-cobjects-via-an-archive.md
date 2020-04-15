---
title: Przechowywanie i ładowanie obiektów CObject za pomocą archiwum
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: f1b59516d5bba13b6f5e006f91d8ebd560543b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372143"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Przechowywanie i ładowanie obiektów CObject za pomocą archiwum

Przechowywanie i `CObject`ładowanie s za pośrednictwem archiwum wymaga dodatkowego rozważenia. W niektórych przypadkach należy `Serialize` wywołać funkcję obiektu, gdzie `CArchive` obiekt `Serialize` jest parametrem wywołania, ** < ** w przeciwieństwie do korzystania z lub **>>** operatora `CArchive`. Ważnym faktem, o których należy `CArchive` **>>** pamiętać, `CObject` jest to, `CRuntimeClass` że operator konstruuje w pamięci na podstawie informacji wcześniej zapisanych w pliku przez archiwum przechowywania.

W związku z tym, **>>** czy używasz `CArchive` ** < ** i operatorów, w porównaniu do `Serialize`wywoływania , zależy `CRuntimeClass` od tego, czy *potrzebne* jest archiwum ładowania do dynamicznego odtworzenia obiektu na podstawie wcześniej przechowywanych informacji. Użyj `Serialize` tej funkcji w następujących przypadkach:

- Podczas deserializacji obiektu, znasz dokładną klasę obiektu wcześniej.

- Podczas deserializacji obiektu, masz już pamięć przydzielona dla niego.

> [!CAUTION]
> W przypadku ładowania obiektu `Serialize` za pomocą funkcji, należy `Serialize` również przechowywać obiekt za pomocą funkcji. Nie przechowuj przy `CArchive` **<<** użyciu operatora, a `Serialize` następnie ładuj `Serialize` za pomocą funkcji `CArchive >>` lub przechowuj za pomocą funkcji, a następnie ładuj za pomocą operatora.

Poniższy przykład ilustruje przypadki:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

Podsumowując, jeśli klasa serializable definiuje `CObject` osadzone jako element członkowski, **>>** *nie* należy używać `CArchive` ** < ** i operatorów dla tego obiektu, ale należy wywołać `Serialize` funkcję zamiast tego. Ponadto jeśli klasa serializable definiuje wskaźnik `CObject` do (lub obiekt `CObject`pochodny od) jako element członkowski, ale konstruuje ten `Serialize`inny obiekt w swoim własnym konstruktorze, należy również wywołać .

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)
