---
title: 'Serializacja: Serializacja obiektu'
ms.date: 11/04/2016
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
ms.openlocfilehash: 5c1106f180c587894283575a82a88e9e18b5c01a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290498"
---
# <a name="serialization-serializing-an-object"></a>Serializacja: Serializacja obiektu

Artykuł [serializacji: Możliwy do serializacji klasy jako możliwej](../mfc/serialization-making-a-serializable-class.md) pokazuje, jak i wybierz klasę serializacji. Po utworzeniu klasy serializacji, serializacji obiektów tej klasy do i z pliku za pośrednictwem [CArchive](../mfc/reference/carchive-class.md) obiektu. W tym artykule opisano:

- [Jest obiekt CArchive](../mfc/what-is-a-carchive-object.md).

- [Dwa sposoby tworzenia obiektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Jak używać obiektu CArchive <\< i >> operatory](../mfc/using-the-carchive-output-and-input-operators.md).

- [Przechowywanie i ładowanie obiektów CObject za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Można pozwolić framework Utwórz archiwum dokumentu do serializacji lub jawnie `CArchive` obiektu samodzielnie. Mogą przesyłać dane między plikiem a możliwy do serializacji obiektu za pomocą <\< i >> operatory `CArchive` lub w niektórych przypadkach, wywołując `Serialize` funkcji `CObject`-klasy pochodnej.

## <a name="see-also"></a>Zobacz także

[Serializacja](../mfc/serialization-in-mfc.md)
