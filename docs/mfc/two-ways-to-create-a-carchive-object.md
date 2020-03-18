---
title: Dwa sposoby tworzenia obiektu CArchive
ms.date: 11/04/2016
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
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442037"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dwa sposoby tworzenia obiektu CArchive

Istnieją dwa sposoby tworzenia obiektu `CArchive`:

- [Niejawne utworzenie obiektu CArchive za pośrednictwem struktury](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Jawne utworzenie obiektu CArchive](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Niejawne utworzenie obiektu CArchive za pośrednictwem struktury

Najbardziej typowym i najprostszym sposobem jest umożliwienie struktury tworzenia `CArchive` obiektu dla dokumentu w imieniu poleceń Zapisz, Zapisz jako i Otwórz w menu plik.

Oto jakie środowisko robi, gdy użytkownik aplikacji wystawia polecenie Zapisz jako z menu plik:

1. Wyświetla okno dialogowe **Zapisz jako** i pobiera nazwę pliku od użytkownika.

1. Otwiera plik o nazwie przez użytkownika jako obiekt `CFile`.

1. Tworzy obiekt `CArchive`, który wskazuje na ten obiekt `CFile`. W przypadku tworzenia obiektu `CArchive` struktura ustawia tryb na "Store" (Write, serializacji), w przeciwieństwie do "Load" (odczyt, deserializacji).

1. Wywołuje funkcję `Serialize` zdefiniowaną w klasie pochodnej `CDocument`, przekazując do niej odwołanie do obiektu `CArchive`.

Funkcja `Serialize` dokumentu następnie zapisuje dane do obiektu `CArchive`, jak wyjaśniono wkrótce. Po powrocie z funkcji `Serialize`, struktura niszczy obiekt `CArchive`, a następnie obiekt `CFile`.

W takim przypadku, Jeśli zezwolisz platformie na utworzenie obiektu `CArchive` dla dokumentu, wszystkie czynności, które należy wykonać, implementują funkcję `Serialize` dokumentu, która zapisuje i odczytuje do i z archiwum. Należy również zaimplementować `Serialize` dla dowolnego obiektu pochodnego `CObject`, który funkcja `Serialize` dokumentu w przekształca bezpośrednio lub pośrednio.

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>Jawne utworzenie obiektu CArchive

Oprócz serializowania dokumentu za pośrednictwem struktury istnieją inne przypadki, w których może być potrzebny `CArchive` obiektu. Na przykład możesz chcieć serializować dane do i ze schowka reprezentowane przez obiekt `CSharedFile`. Lub można użyć interfejsu użytkownika do zapisywania pliku, który jest inny niż ten, który jest oferowany przez platformę. W takim przypadku można jawnie utworzyć obiekt `CArchive`. Wykonuje się to tak samo jak w przypadku platformy, wykonując poniższą procedurę.

#### <a name="to-explicitly-create-a-carchive-object"></a>Aby jawnie utworzyć obiekt CArchive

1. Utwórz obiekt `CFile` lub obiekt pochodzący z `CFile`.

1. Przekaż obiekt `CFile` do konstruktora dla `CArchive`, jak pokazano w następującym przykładzie:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Drugim argumentem konstruktora `CArchive` jest wartość wyliczana określająca, czy archiwum będzie używane do przechowywania lub ładowania danych do lub z pliku. Funkcja `Serialize` obiektu sprawdza ten stan, wywołując funkcję `IsStoring` dla obiektu archiwum.

Po zakończeniu przechowywania lub ładowania danych do lub z obiektu `CArchive`, zamknij go. Mimo że obiekty `CArchive` (i `CFile`) automatycznie zamkną archiwum (i plik), dobrym rozwiązaniem jest to, że jest to bardziej jawne, ponieważ sprawia, że odzyskiwanie z błędów jest łatwiejsze. Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [wyjątki artykułów: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Aby zamknąć obiekt CArchive

1. Poniższy przykład ilustruje sposób zamykania obiektu `CArchive`:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)
