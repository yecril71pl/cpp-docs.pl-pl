---
title: Błąd PRJ0006 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 264b2f90a2d778b1545117ce5c3b1272626ebad6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073255"
---
# <a name="project-build-error-prj0006"></a>Błąd PRJ0006 kompilacji projektu

Nie można otworzyć pliku tymczasowego 'Plik'. Upewnij się, że plik istnieje i że katalog jest nie zabezpieczony przed zapisem.

Visual C++ nie można utworzyć pliku tymczasowego w procesie kompilacji. Przyczyny są między innymi:

- Nie katalogu tymczasowego.

- Tylko do odczytu katalogu tymczasowego.

- Brak miejsca na dysku.

- $(IntDir) folder jest tylko do odczytu lub zawiera pliki tymczasowe, które są przeznaczone tylko do odczytu.

Ten błąd wystąpi następujący błąd PRJ0007: nie można utworzyć katalogu wyjściowego 'katalog'. Błąd PRJ0007 oznacza, że nie można utworzyć katalogu $(IntDir) obszaru tworzenie tymczasowo plików będą również zakończyć się niepowodzeniem.

Pliki tymczasowe są tworzone w każdym przypadku, gdy należy określić:

- Plik odpowiedzi.

- Niestandardowego kroku kompilacji.

- To zdarzenie kompilacji.