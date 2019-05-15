---
title: Kreator dostawcy interfejsu OLE DB ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 91384d6c61368ee56ed303622e5c1bdfad09bd8a
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706964"
---
# <a name="atl-ole-db-provider-wizard"></a>Kreator dostawcy interfejsu OLE DB ATL

::: moniker range="vs-2019"

Ten kreator nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestrowania generowane przez kreatora, będą rejestrować jego składników modelu COM, w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.

W poniższej tabeli opisano opcje ATL OLE DB Provider kreatora:

- **Krótka nazwa**

   Wpisz krótką nazwę dostawcy, który ma zostać utworzony. Pozostałe pola edycji kreatora zostaną wypełnione automatycznie oparte na w tym miejscu wpisz. Jeśli chcesz, możesz edytować pozostałe pola nazw.

- **Coclass**

   Nazwa klasy coclass. Nazwa identyfikatora ProgID zostanie zmieniona na pasują do tej nazwy.

- **Opartego na atrybutach**

   Ta opcja określa, czy Kreator utworzy klasy dostawców przy użyciu atrybutów lub deklaracji szablonu. Po wybraniu tej opcji, kreator używa atrybutów zamiast deklaracji szablonu (jest to opcja domyślna Jeśli zostało utworzone w projekcie z atrybutami). Po usunięciu zaznaczenia tej opcji, kreator używa deklaracji szablonu zamiast atrybutów (jest to opcja domyślna, jeśli utworzono projekt bezatrybutowego).

   Wybranie tej opcji podczas tworzenia projektu bezatrybutowego, Kreator wyświetli ostrzeżenie, zostaną przekonwertowane na projekcie z atrybutami i zapyta, czy chcesz kontynuować, lub nie projektu.

- **ProgID**

   Identyfikator ProgID lub identyfikator programowy, to ciąg tekstowy, który aplikacja może użyć zamiast identyfikatora GUID. Nazwa identyfikatora ProgID ma formę *NazwaProjektu.nazwaklasycoclass*.

- **Wersja**

   Numer wersji dostawcy. Domyślnym ustawieniem jest 1.

- **Klasa źródła danych**

   Nazwa klasy źródła danych w formularzu C*Shortname*źródła.

- **Plik .h klasy źródła danych**

   Plik nagłówkowy klasy źródła danych. Można zmienić nazwę tego pliku lub wybierz istniejący plik nagłówkowy.

- **Klasy sesji**

   Nazwa klasy sesji formularza C*Shortname*sesji.

- **Plik .h klasy sesji**

   Plik nagłówkowy klasy sesji. Można zmienić nazwę tego pliku lub wybierz istniejący plik nagłówkowy.

- **Klasa polecenia**

   Nazwa klasy poleceń formularza C*Shortname*polecenia.

- **Plik .h klasy poleceń**

   Plik nagłówkowy klasy poleceń. Ta nazwa nie może być edytowany i zależy od nazwy pliku nagłówkowego zestawu wierszy.

- **Klasy zestawów wierszy**

   Nazwa klasy zestawu wierszy formularza C*Shortname*zestawu wierszy.

- **Plik .h klasy zestawu wierszy**

   Plik nagłówkowy klasy zestawu wierszy. Można zmienić nazwę tego pliku lub wybierz istniejący plik nagłówkowy.

- **Plik CPP zestawu wierszy**

   Plik implementacji dostawcy. Można zmienić nazwę tego pliku lub wybierz istniejący plik implementacji.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Dostawcy ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-provider.md)
