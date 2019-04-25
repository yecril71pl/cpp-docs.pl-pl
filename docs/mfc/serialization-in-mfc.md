---
title: Serializacja w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: 5c7dec140635b6d83bdae936d1bb0cef144f825b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308216"
---
# <a name="serialization-in-mfc"></a>Serializacja w MFC

W tym artykule wyjaśniono, że mechanizm serializacji, podany w Microsoft Foundation Class Library (MFC) umożliwia zachowanie obiektów pomiędzy uruchomieniami programu.

Serializacja jest proces wpisywanie lub odczytywanie obiekt do lub z nośnika z magazynu trwałego, takich jak pliku na dysku. Serializacja jest idealnym rozwiązaniem dla sytuacji, w których jest potrzebne do obsługi stanu danych strukturalnych (na przykład C++ klasy lub struktury) w trakcie lub po zakończeniu wykonywania programu. Używanie obiektów serializacji dostarczonych przez MFC umożliwia to możliwe w standardowych i spójny sposób zwalniający użytkownika z konieczności ręcznego wykonywania operacji na plikach.

MFC udostępnia wbudowaną obsługę serializacji w klasie `CObject`. W efekcie wszystkie klasy pochodne klasy `CObject` korzystać z zalet `CObject`przez Protokół serializacji.

Podstawowa koncepcja serializacji jest, że obiekt powinien móc zapisać jego bieżący stan, zazwyczaj wskazywany przez wartość jego zmiennych składowych w magazynie trwałym. Później obiekt można ponownie utworzyć poprzez czytanie, lub deserializację, stanu obiektu z magazynu. Serializacja obsługuje wszystkie szczegóły obiektu wskaźniki i odwołania cykliczne do obiektów, które są używane podczas serializacji obiektu. Kluczowym punktem jest odpowiedzialna za odczytywanie i zapisywanie własną stan samego obiektu. W związku z tym klasa może podlegać serializacji, musi on implementować operacje podstawowe serializacji. Jak pokazano w grupie serializacji, artykułów, to łatwo dodać tę funkcjonalność do klasy.

MFC używa obiektu `CArchive` klasy jako pośrednik pomiędzy nośnika magazynowania i obiektu do zserializowania. Ten obiekt jest skojarzony z zawsze `CFile` obiektu, z którego uzyskuje informacje niezbędne do serializacji, łącznie z nazwą pliku i tego, czy Żądana operacja jest do odczytu lub zapisu. Można użyć obiektu, który wykonuje operację serializacji `CArchive` obiektu bez względu na charakter nośnika magazynowania.

A `CArchive` obiekt używa przeciążona wstawiania (**<\<**) i wyodrębniania (**>>**) operatory do wykonania, zapisywanie i odczytywanie operacji. Aby uzyskać więcej informacji, zobacz [przechowywanie i ładowanie obiektów CObject za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md) w artykule serializacji: Serializacja obiektu.

> [!NOTE]
>  Nie należy mylić `CArchive` klasie z atrybutem klasy iostream ogólnego przeznaczenia, które służą do sformatowanego tekstu tylko. `CArchive` Klasa jest binarny format serializacji obiektów.

Jeśli chcesz, można pominąć serializacji MFC, aby utworzyć własny mechanizm do trwałego magazynu danych. Należy przesłonić funkcje składowych klasy, które inicjują serializacji na polecenie użytkownika. Zobacz Omówienie w [techniczne 22 Uwaga](../mfc/tn022-standard-commands-implementation.md) id_file_open — id_file_save — i id_file_save_as — standardowych poleceń.

Następujące artykuły obejmuje dwa główne zadania wymagane do serializacji:

- [Serializacja: Możliwy do serializacji klasy jako możliwej](../mfc/serialization-making-a-serializable-class.md)

- [Serializacja: Serializacja obiektu](../mfc/serialization-serializing-an-object.md)

Artykuł [serializacji: Serializacja programu vs. Baza danych wejściowych/wyjściowych](../mfc/serialization-serialization-vs-database-input-output.md) opisano po serializacji jest właściwa metoda wejścia/wyjścia w aplikacjach baz danych.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CArchive](../mfc/reference/carchive-class.md)<br/>
[Klasa CObject](../mfc/reference/cobject-class.md)<br/>
[Klasa CDocument](../mfc/reference/cdocument-class.md)<br/>
[Klasa CFile](../mfc/reference/cfile-class.md)
