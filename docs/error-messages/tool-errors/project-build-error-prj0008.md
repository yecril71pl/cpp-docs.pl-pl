---
title: Błąd PRJ0008 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 696b77e9906b231a680027a3faaf23e53d8fb6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525909"
---
# <a name="project-build-error-prj0008"></a>Błąd PRJ0008 kompilacji projektu

Nie można usunąć pliku 'Plik'.

**Upewnij się, że plik nie jest otwarty przez inny proces i nie jest zabezpieczony przed zapisem.**

Podczas ponownej kompilacji lub czyszczenia, Visual C++ usuwa wszystkie znane plików pośrednich i wynikowych dla kompilacji, a także wszystkie pliki, które są zgodne ze specyfikacjami symbolu wieloznacznego w **rozszerzenia do usunięcia podczas oczyszczania** właściwość [ogólne Strona właściwości ustawień konfiguracji](../../ide/general-property-page-project.md).

Zostanie wyświetlony ten błąd, jeśli Visual C++ nie jest w stanie usunąć plik. Aby naprawić błąd, tworzenie pliku i jego katalogu zapisywalny dla użytkownika podczas kompilacji.