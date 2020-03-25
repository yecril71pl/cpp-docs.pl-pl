---
title: Błąd PRJ0008 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 7d1c11ab7539f25d371c0bfbd2853b6155c9661c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192960"
---
# <a name="project-build-error-prj0008"></a>Błąd PRJ0008 kompilacji projektu

Nie można usunąć pliku "File".

**Upewnij się, że plik nie jest otwarty przez inny proces i nie jest chroniony przed zapisem.**

Podczas odbudowywania lub czyszczenia, Wizualizacja C++ usuwa wszystkie znane pliki pośrednich i wyjściowych dla kompilacji, a także wszystkie pliki, które są zgodne ze specyfikacją symboli wieloznacznych w **rozszerzeniach do usuwania przy czyszczeniu** właściwości na [stronie właściwości ustawienia konfiguracji ogólnej](../../build/reference/general-property-page-project.md).

Ten błąd zostanie wyświetlony, jeśli element C++ Visual nie może usunąć pliku. Aby rozwiązać ten problem, wprowadź plik i jego katalog zapisywalny dla użytkownika wykonującego kompilację.
