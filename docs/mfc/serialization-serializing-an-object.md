---
title: 'Serializacja: Serializacja obiektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e05cce1132b180ac8f1350b68d951d776a62315f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381091"
---
# <a name="serialization-serializing-an-object"></a>Serializacja: serializacja obiektu

Artykuł [serializacji: możliwy do serializacji klasy jako możliwej](../mfc/serialization-making-a-serializable-class.md) pokazuje, jak i wybierz klasę serializacji. Po utworzeniu klasy serializacji, serializacji obiektów tej klasy do i z pliku za pośrednictwem [CArchive](../mfc/reference/carchive-class.md) obiektu. W tym artykule opisano:

- [Jest obiekt CArchive](../mfc/what-is-a-carchive-object.md).

- [Dwa sposoby tworzenia obiektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md).

- [Jak używać obiektu CArchive <\< i >> operatory](../mfc/using-the-carchive-output-and-input-operators.md).

- [Przechowywanie i ładowanie obiektów CObject za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Można pozwolić framework Utwórz archiwum dokumentu do serializacji lub jawnie `CArchive` obiektu samodzielnie. Mogą przesyłać dane między plikiem a możliwy do serializacji obiektu za pomocą <\< i >> operatory `CArchive` lub w niektórych przypadkach, wywołując `Serialize` funkcji `CObject`-klasy pochodnej.

## <a name="see-also"></a>Zobacz też

[Serializacja](../mfc/serialization-in-mfc.md)

