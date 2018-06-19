---
title: Przechowywanie i ładowanie obiektów CObjects za pomocą archiwum | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fe5cc426e3494117bff98577f02178709a2588f3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380731"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Przechowywanie i ładowanie obiektów CObject za pomocą archiwum
Przechowywanie i ładowanie `CObject`s za pomocą archiwum wymaga dodatkowego rozważenia. W niektórych przypadkach należy wywołać `Serialize` funkcji obiektu, którym `CArchive` obiektu jest parametrem `Serialize` wywołanie, a nie za pomocą **< \<** lub **>>** operator `CArchive`. Jest to ważne fakt, do którego należy wziąć pod uwagę, że `CArchive` **>>** konstrukcji operator `CObject` w pamięci na podstawie `CRuntimeClass` informacji wcześniej zapisane w pliku przez zapisywanie archiwum.  
  
 W związku z tym, czy używasz `CArchive` **< \<** i **>>** operatorów, w porównaniu z wywołaniem `Serialize`, zależy od tego, czy użytkownik *muszą* archiwum ładowania dynamicznie odtworzenie obiekt na podstawie zapisanych wcześniej `CRuntimeClass` informacji. Użyj `Serialize` funkcji w następujących przypadkach:  
  
-   Podczas deserializacji obiektu, znasz dokładnego klasy obiektu wcześniej.  
  
-   Podczas deserializacji obiektu, masz już pamięci przydzielona dla niego.  
  
> [!CAUTION]
>  Po załadowaniu obiekt przy użyciu `Serialize` funkcji, należy także zapisać obiekt przy użyciu `Serialize` funkcji. Nie należy przechowywać za pomocą `CArchive` **<<** operatora, a następnie użyć obciążenia `Serialize` funkcji lub magazynu przy użyciu `Serialize` funkcji, a następnie za pomocą **CArchive >>** operatora.  
  
 Poniższy przykład przedstawia przypadkach:  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 Podsumowując, jeśli możliwy do serializacji klasy definiuje osadzonych **CObjec**t jako element członkowski, należy *nie* użyj `CArchive` **< \<** i **>>** operatory dla tego obiektu, ale powinny wywoływać `Serialize` zamiast tego działania. Ponadto jeśli możliwy do serializacji klasy definiuje wskaźnik do `CObject` (lub typ pochodzący od obiektu `CObject`) jako element członkowski, ale konstrukcji tego innego obiektu w jego własnej konstruktora, należy także wywołać `Serialize`.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)

