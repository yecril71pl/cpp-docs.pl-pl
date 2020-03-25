---
title: Błąd PRJ0006 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: 816355276a203adba1401841ce02eb94a18085b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192786"
---
# <a name="project-build-error-prj0006"></a>Błąd PRJ0006 kompilacji projektu

Nie można otworzyć pliku tymczasowego "File". Upewnij się, że plik istnieje i że katalog nie jest chroniony przed zapisem.

Wizualizacja C++ nie może utworzyć pliku tymczasowego podczas procesu kompilacji. Przyczyny są między innymi następujące:

- Brak katalogu tymczasowego.

- Katalog tymczasowy tylko do odczytu.

- Brak miejsca na dysku.

- Folder $ (IntDir) jest w trybie tylko do odczytu lub zawiera pliki tymczasowe, które są tylko do odczytu.

Ten błąd wystąpi również po wystąpieniu błędu PRJ0007: nie można utworzyć katalogu wyjściowego "Directory". Błąd PRJ0007 oznacza, że nie można utworzyć katalogu $ (IntDir), co oznacza, że tworzenie tymczasowego plików również zakończy się niepowodzeniem.

Pliki tymczasowe są tworzone po każdym określeniu:

- Plik odpowiedzi.

- Niestandardowy krok kompilacji.

- Zdarzenie kompilacji.
