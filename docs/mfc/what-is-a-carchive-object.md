---
title: Co to jest obiekt CArchive
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 0a78385c81c43a4b0c925bbe89ccd3937873ee8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446020"
---
# <a name="what-is-a-carchive-object"></a>Co to jest obiekt CArchive

Obiekt `CArchive` zapewnia bezpieczny dla typu mechanizm buforowania do zapisywania lub odczytywania serializowanych obiektów do lub z `CFile` obiektu. Zazwyczaj obiekt `CFile` reprezentuje plik dyskowy; Jednak może to również być plik pamięci (`CSharedFile` Object), prawdopodobnie reprezentujący schowek.

Dany obiekt `CArchive` albo przechowuje (zapisuje, deserializacji) dane lub ładuje (odczytuje, deserializacji) dane, ale nigdy nie obu. Okres istnienia obiektu `CArchive` jest ograniczony do jednego przebiegu przez zapisanie obiektów do pliku lub odczytywanie obiektów z pliku. W ten sposób do serializacji danych do pliku są wymagane dwa po nim obiekty `CArchive`, a następnie deserializacji z powrotem z pliku.

Gdy archiwum przechowuje obiekty do pliku, archiwum dołącza nazwę `CRuntimeClass` do obiektów. Następnie, gdy inne archiwum ładuje obiekty z pliku do pamięci, obiekty pochodne `CObject`są dynamicznie ponownie konstruowane na podstawie `CRuntimeClass` obiektów. Dany obiekt może być przywoływany więcej niż raz, ponieważ jest zapisywany w pliku przez archiwum przechowujące. Archiwum ładowania, jednak ponownie konstruuje obiekt tylko raz. Szczegółowe informacje na temat sposobu dołączania archiwum `CRuntimeClass` informacji do obiektów i odbudowy obiektów, biorąc pod uwagę możliwe wiele odwołań, są opisane w [uwagi technicznej 2](../mfc/tn002-persistent-object-data-format.md).

Gdy dane są serializowane do archiwum, archiwum zbiera dane do momentu zapełnienia buforu. Następnie archiwum zapisuje bufor w obiekcie `CFile` wskazywanym przez obiekt `CArchive`. Podobnie podczas odczytywania danych z archiwum dane są odczytywane z pliku do bufora, a następnie z bufora do deserializowanego obiektu. Buforowanie zmniejsza liczbę przypadków, gdy dysk twardy jest odczytywany fizycznie, co poprawia wydajność aplikacji.

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)
