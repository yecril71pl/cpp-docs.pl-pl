---
title: Błąd PRJ0035 kompilacji projektu
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: e221fd85f1260ed04d49b43dea3d13407f504847
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472348"
---
# <a name="project-build-error-prj0035"></a>Błąd PRJ0035 kompilacji projektu

> Plik XML '*pliku*' zawiera znaki unikodowe, które nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.
>
> *UNICODE zawartość pliku*

*plik* jest plikiem XML, utworzony jako wiersz polecenia do narzędzia Web Deployment.

System projektu znaleziono znaki Unicode w niektórych właściwości na stronie właściwości wdrażania w Internecie, prawidłowo niemożliwymi do ANSI.

Rozwiązanie dotyczące tego błędu jest aktualizacji wartości właściwości, aby użyć ANSI lub Zainstaluj stronę kodową na swoim komputerze i jest ustawiony jako domyślny system.