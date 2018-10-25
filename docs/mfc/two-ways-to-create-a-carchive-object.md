---
title: Dwa sposoby tworzenia obiektu CArchive | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 630cdd1614aa19ec3a5a654d7dc4bfe7336ce027
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080588"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dwa sposoby tworzenia obiektu CArchive

Istnieją dwa sposoby tworzenia `CArchive` obiektu:

- [Operacje niejawnego tworzenia obiektu CArchive za pośrednictwem programu framework](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Jawne utworzenie obiektu CArchive](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Operacje niejawnego tworzenia obiektu CArchive za pośrednictwem programu Framework

Najbardziej powszechną i Najłatwiejszą, sposób jest umożliwienie framework tworzenie `CArchive` obiektu dokumentu w imieniu Zapisz, Zapisz jako i polecenia Otwórz menu Plik.

To co platformę, gdy użytkownik aplikacji generuje polecenia Zapisz jako, w menu Plik:

1. Przedstawia informacje o **Zapisz jako** okno dialogowe i pobiera nazwy pliku od użytkownika.

1. Otwiera plik o nazwie określonej przez użytkownika jako `CFile` obiektu.

1. Tworzy `CArchive` obiektu, który wskazuje na to `CFile` obiektu. Podczas tworzenia `CArchive` obiekt, w ramach Ustawia tryb na "przechowywać" (zapis, serializować) zamiast "ładowanie" (Odczyt, deserializacji).

1. Wywołania `Serialize` funkcję zdefiniowaną w swojej `CDocument`-klasy, przekazywanie jej przez odwołanie do `CArchive` obiektu.

Twój dokument `Serialize` funkcja następnie zapisuje dane do `CArchive` obiektu, zgodnie z objaśnieniem wkrótce. Po powrocie z Twojej `Serialize` niszczy platformę funkcji `CArchive` obiektu a następnie `CFile` obiektu.

W związku z tym jeśli zezwolisz framework tworzenie `CArchive` obiekt dokumentu, wystarczy zrobić to implementacja tego dokumentu `Serialize` funkcja, która zapisuje i odczytuje do i z archiwum. Również musiał zostać zaimplementowany `Serialize` dla każdego `CObject`-obiektami wywodzącymi, dokumentu `Serialize` funkcji z kolei serializuje bezpośrednio lub pośrednio.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a> Jawne utworzenie obiektu CArchive

Oprócz serializacji dokumentu przez platformę, są inne sytuacje, kiedy może być konieczne `CArchive` obiektu. Na przykład możesz chcieć serializacja danych do i z Schowka, reprezentowane przez `CSharedFile` obiektu. Możesz też użyć interfejsu użytkownika do zapisywania pliku, który jest inny niż oferowany przez platformę. W takim przypadku można jawnie utworzyć `CArchive` obiektu. W tym taki sam sposób, który jest struktura, korzystając z następującej procedury.

#### <a name="to-explicitly-create-a-carchive-object"></a>Aby jawnie tworzenia obiektu CArchive

1. Konstruowania `CFile` lub obiektu pochodną `CFile`.

1. Przekaż `CFile` obiekt do konstruktora dla `CArchive`, jak pokazano w poniższym przykładzie:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Drugi argument `CArchive` Konstruktor jest wyliczany określający czy archiwum będą używane do przechowywania lub podczas ładowania danych do lub z pliku. `Serialize` Funkcja obiektu sprawdza, czy ten stan, wywołując `IsStoring` funkcji dla obiektu archiwum.

Po zakończeniu, przechowywanie i ładowanie danych do lub z `CArchive` obiektów, zamknij go. Mimo że `CArchive` (i `CFile`) obiektów zostanie automatycznie zamknięte archiwum (i plik), jest dobrą praktyką, aby jawnie w tym celu, ponieważ ułatwia odzyskiwanie z błędami. Aby uzyskać więcej informacji na temat obsługi błędów, zobacz artykuł [wyjątki: wyjątki połowowe i usuwanie](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Aby zamknąć obiektu CArchive

1. Poniższy przykład ilustruje sposób zamknięcia `CArchive` obiektu:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)

