---
title: Błąd PRJ0008 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359491"
---
# <a name="project-build-error-prj0008"></a>Błąd PRJ0008 kompilacji projektu

Nie można usunąć pliku 'Plik'.

**Upewnij się, że plik nie jest otwarty przez inny proces i nie jest zabezpieczony przed zapisem.**

Podczas ponownej kompilacji lub czyszczenia, Visual C++ usuwa wszystkie znane plików pośrednich i wynikowych dla kompilacji, a także wszystkie pliki, które są zgodne ze specyfikacjami symbolu wieloznacznego w **rozszerzenia do usunięcia podczas oczyszczania** właściwość [ogólne Strona właściwości ustawień konfiguracji](../../build/reference/general-property-page-project.md).

Zostanie wyświetlony ten błąd, jeśli Visual C++ nie jest w stanie usunąć plik. Aby naprawić błąd, tworzenie pliku i jego katalogu zapisywalny dla użytkownika podczas kompilacji.