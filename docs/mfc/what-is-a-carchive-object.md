---
title: Co to jest obiekt CArchive | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CArchive
dev_langs: C++
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2fe145a2bfac01bd201284bbbaa8250ee20b3612
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="what-is-a-carchive-object"></a>Co to jest obiekt CArchive
A `CArchive` obiektu zapewnia bezpieczny mechanizm buforowania do zapisywania lub odczytywania obiekty możliwe do serializacji do lub z `CFile` obiektu. Zazwyczaj `CFile` obiekt reprezentuje pliku na dysku; jednak również może być pliku pamięci (`CSharedFile` obiektu), być może reprezentujący Schowka.  
  
 Biorąc pod uwagę `CArchive` obiekt albo magazynów (zapisuje, serializuje) danych lub obciążeń (odczytuje, deserializuje) dane, ale nie oba. Czas życia `CArchive` obiektu jest ograniczony do jednego przekazywania zapisywania obiektów do pliku lub odczytywania obiektów z pliku. W związku z tym dwóch kolejno tworzone `CArchive` obiekty są wymagane do serializowania danych do pliku, a następnie do deserializacji z pliku.  
  
 Jeśli archiwum przechowuje obiekty do pliku, dołącza archiwum `CRuntimeClass` nazwie do obiektów. Następnie, po innym archiwum ładuje obiekty z pliku do pamięci, `CObject`-obiekty pochodne są dynamicznie odtworzyć na podstawie `CRuntimeClass` obiektów. Podany obiekt można odwoływać się tylko jeden raz podczas zapisywania do pliku przez zapisywanie archiwum. Archiwum ładowania, jednak będą rekonstrukcji obiektu tylko raz. Szczegółowe informacje o sposobie dołącza archiwum `CRuntimeClass` opisano informacje, aby obiekty i niezamrożone, biorąc pod uwagę możliwe wiele odwołań w [techniczne Uwaga 2](../mfc/tn002-persistent-object-data-format.md).  
  
 Jak dane są serializowane archiwum, archiwum zebrane dane do momentu swojego bufora jest pełny. Następnie archiwum zapisuje buforu do `CFile` obiekt wskazywany przez `CArchive` obiektu. Podobnie jak odczytać danych z archiwum odczytuje dane z pliku do buforu, a następnie z buforu obiektowi zdeserializowany. To buforowanie zmniejsza liczbę razy na dysku twardym jest fizycznie do odczytu, co poprawia wydajność aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja: Serializacja obiektu](../mfc/serialization-serializing-an-object.md)

