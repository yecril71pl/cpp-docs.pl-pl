---
title: Kreator dostawcy interfejsu OLE DB ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.provider.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6857bf80aaaad36b4dcfc4fbf1330eccd03f971a
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250357"
---
# <a name="atl-ole-db-provider-wizard"></a>Kreator dostawcy interfejsu OLE DB ATL

Ten kreator tworzy klas, które tworzą dostawcy OLE DB.

> [!WARNING]
> W programie Visual Studio 2017 w wersji 15.9 tego kreatora kodu jest przestarzały i zostanie usunięta w przyszłych wersjach programu Visual Studio. Ten kreator jest rzadko używana. Ogólna obsługa biblioteki ATL i MFC nie ulega zmianie poprzez usunięcie tego kreatora. Jeśli chcesz przekazać opinię dotyczącą tego wycofywania, wypełnij [w ramach tej ankiety](https://www.surveymonkey.com/r/QDWKKCN). Twoja opinia ma znaczenie dla nas.


## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestrowania generowane przez kreatora, będą rejestrować jego składników modelu COM, w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.

W poniższej tabeli opisano opcje ATL OLE DB Provider kreatora:

- **Krótka nazwa**

   Wpisz krótką nazwę dostawcy, który ma zostać utworzony. Pozostałe pola edycji kreatora zostaną wypełnione automatycznie oparte na w tym miejscu wpisz. Jeśli chcesz, możesz edytować pozostałe pola nazw.

- **Klasa coclass**

   Nazwa klasy coclass. Nazwa identyfikatora ProgID zostanie zmieniona na pasują do tej nazwy.

- **Opartego na atrybutach**

   Ta opcja określa, czy Kreator utworzy klasy dostawców przy użyciu atrybutów lub deklaracji szablonu. Po wybraniu tej opcji, kreator używa atrybutów zamiast deklaracji szablonu (jest to opcja domyślna Jeśli zostało utworzone w projekcie z atrybutami). Po usunięciu zaznaczenia tej opcji, kreator używa deklaracji szablonu zamiast atrybutów (jest to opcja domyślna, jeśli utworzono projekt bezatrybutowego).

   Wybranie tej opcji podczas tworzenia projektu bezatrybutowego, Kreator wyświetli ostrzeżenie, zostaną przekonwertowane na projekcie z atrybutami i zapyta, czy chcesz kontynuować, lub nie projektu.

- **Identyfikator programu**

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

## <a name="see-also"></a>Zobacz też

[Dostawcy ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-provider.md)

