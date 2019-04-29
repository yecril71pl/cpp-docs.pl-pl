---
title: Błąd PRJ0006 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359660"
---
# <a name="project-build-error-prj0006"></a>Błąd PRJ0006 kompilacji projektu

Nie można otworzyć pliku tymczasowego 'Plik'. Upewnij się, że plik istnieje i że katalog jest nie zabezpieczony przed zapisem.

Visual C++ nie można utworzyć pliku tymczasowego w procesie kompilacji. Przyczyny są między innymi:

- Nie katalogu tymczasowego.

- Tylko do odczytu katalogu tymczasowego.

- Brak miejsca na dysku.

- $(IntDir) folder jest tylko do odczytu lub zawiera pliki tymczasowe, które są przeznaczone tylko do odczytu.

Ten błąd wystąpi również następujący błąd PRJ0007: Nie można utworzyć katalogu wyjściowego 'katalog'. Błąd PRJ0007 oznacza, że nie można utworzyć katalogu $(IntDir) obszaru tworzenie tymczasowo plików będą również zakończyć się niepowodzeniem.

Pliki tymczasowe są tworzone w każdym przypadku, gdy należy określić:

- Plik odpowiedzi.

- Niestandardowego kroku kompilacji.

- To zdarzenie kompilacji.