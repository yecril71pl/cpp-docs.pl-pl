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
ms.openlocfilehash: 3439857f14f4c4fa78aa2df3e3da8e5c8941938d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="serialization-serializing-an-object"></a>Serializacja: serializacja obiektu
Artykuł [serializacja: ustawianie klasy jako możliwy do serializacji](../mfc/serialization-making-a-serializable-class.md) pokazano, jak utworzyć klasę serializacji. Po utworzeniu klasy możliwej do serializacji, może serializować obiektów klas do i z pliku za pośrednictwem [CArchive](../mfc/reference/carchive-class.md) obiektu. W tym artykule opisano:  
  
-   [Jest obiekt CArchive](../mfc/what-is-a-carchive-object.md).  
  
-   [Dwa sposoby tworzenia CArchive](../mfc/two-ways-to-create-a-carchive-object.md).  
  
-   [Jak używać CArchive <\< i >> operatory](../mfc/using-the-carchive-output-and-input-operators.md).  
  
-   [Przechowywanie i ładowanie obiektów CObject za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 Możesz pozwolić, aby framework utworzyć archiwum dokumentu do serializacji lub jawnie `CArchive` obiekt samodzielnie. Przesyłania danych między plikiem a możliwy do serializacji obiektu przy użyciu <\< i >> operatory `CArchive` lub, w niektórych przypadkach, wywołując `Serialize` funkcji `CObject`-klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja](../mfc/serialization-in-mfc.md)

