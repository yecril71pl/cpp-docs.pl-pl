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
ms.openlocfilehash: 368421a86d6ff6fc70455edd0ea9a32e05645007
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446364"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Przechowywanie i ładowanie obiektów CObject za pomocą archiwum

Przechowywanie i ładowanie `CObject`s za pośrednictwem archiwum wymaga dodatkowej uwagi. W niektórych przypadkach należy wywołać funkcję `Serialize` obiektu, gdzie obiekt `CArchive` jest parametrem wywołania `Serialize`, w przeciwieństwie do użycia operatora **<\<** lub **>>** `CArchive`. Należy pamiętać, że operator **>>** `CArchive` konstruuje `CObject` w pamięci na podstawie `CRuntimeClass` informacji poprzednio zapisywanych w pliku przez archiwum przechowujące.

W związku z tym, niezależnie od tego, czy jest używane `CArchive` **<\<** i operatory **>>** , a w przeciwieństwie do `Serialize`, zależy od tego, czy *potrzebujesz* archiwum ładowania do dynamicznego odbudowy obiektu na podstawie wcześniej przechowywanych informacji `CRuntimeClass`. Użyj funkcji `Serialize` w następujących przypadkach:

- Podczas deserializacji obiektu należy wcześniej znać dokładnie klasę obiektu.

- Podczas deserializacji obiektu masz już przydzieloną pamięć.

> [!CAUTION]
>  Jeśli załadujesz obiekt za pomocą funkcji `Serialize`, musisz również zapisać obiekt za pomocą funkcji `Serialize`. Nie przechowuj przy użyciu `CArchive` operatora **<<** , a następnie Ładuj przy użyciu funkcji `Serialize` lub przechowuj przy użyciu funkcji `Serialize`, a następnie załaduj przy użyciu operatora `CArchive >>`.

Poniższy przykład ilustruje przypadki:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

Podsumowując, jeśli klasa, której można serializować, definiuje osadzoną `CObject` jako element członkowski, *nie* należy używać `CArchive` **<\<** i **>>** dla tego obiektu, ale powinien zamiast tego wywołać funkcję `Serialize`. Ponadto, jeśli Klasa możliwa do serializacji definiuje wskaźnik do `CObject` (lub obiektu pochodnego od `CObject`) jako elementu członkowskiego, ale konstruuje ten inny obiekt we własnym konstruktorze, należy również wywołać `Serialize`.

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)
