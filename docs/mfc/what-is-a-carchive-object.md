---
title: Co to jest obiekt CArchive
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 4bae451168449ce3e120ba9d172a615864ac2157
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270400"
---
# <a name="what-is-a-carchive-object"></a>Co to jest obiekt CArchive

A `CArchive` obiektu udostępnia mechanizm buforowania bezpieczny dla wpisywanie lub odczytywanie obiekty możliwe do serializacji lub wejściowych `CFile` obiektu. Zazwyczaj `CFile` obiekt reprezentuje plik dysku; Jednakże, również może być pliku pamięci (`CSharedFile` obiektu), być może reprezentujący Schowka.

Biorąc pod uwagę `CArchive` obiektu albo magazynów (zapisuje, serializuje) danych lub obciążeń (odczytuje, deserializuje) dane, ale nie oba. Czas życia `CArchive` obiektu jest ograniczona do jednego przekazywania zapisywania obiektów do pliku lub odczytywania obiektów z pliku. W związku z tym, dwa kolejno tworzone `CArchive` obiekty są wymagane do serializowania danych do pliku, a następnie zdeserializuj ją z kopii pliku.

Jeśli archiwum przechowuje obiektów do pliku, archiwum dołącza `CRuntimeClass` nazwy do obiektów. Następnie, po innej archiwum ładuje obiekty z pliku do pamięci, `CObject`— obiekty pochodne są dynamicznie odtworzone, na podstawie `CRuntimeClass` obiektów. Danego obiektu mogą być używane więcej niż jeden raz, ponieważ jest ona zapisywana w pliku przez zapisywanie archiwum. Ładowanie archiwum, jednak będzie odtworzenie obiektu tylko raz. Szczegółowe informacje dotyczące sposobu dołącza archiwum `CRuntimeClass` informacje na temat obiektów i obiekty niezamrożone, biorąc pod uwagę możliwe wiele odwołań są opisane w [Technical Preview 2 Uwaga](../mfc/tn002-persistent-object-data-format.md).

Jak danych jest serializowana do archiwum, archiwum gromadzi dane, do momentu zapełnienia buforu. A następnie archiwum zapisuje jego buforu `CFile` obiekt wskazywany przez `CArchive` obiektu. Podobnie jak można odczytywać dane z archiwum, odczytuje dane z pliku do buforu, a następnie z buforu do obiektu po deserializacji. Tej buforowanie zmniejsza liczbę przypadków, gdy na dysku twardym jest fizycznie do odczytu, co poprawia wydajność aplikacji.

## <a name="see-also"></a>Zobacz także

[Serializacja: Serializacja obiektu](../mfc/serialization-serializing-an-object.md)
