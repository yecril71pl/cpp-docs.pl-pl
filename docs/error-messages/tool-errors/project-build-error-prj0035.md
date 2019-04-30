---
title: Błąd PRJ0035 kompilacji projektu
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: e221fd85f1260ed04d49b43dea3d13407f504847
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345293"
---
# <a name="project-build-error-prj0035"></a>Błąd PRJ0035 kompilacji projektu

> Plik XML '*pliku*' zawiera znaki unikodowe, które nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.
>
> *UNICODE zawartość pliku*

*plik* jest plikiem XML, utworzony jako wiersz polecenia do narzędzia Web Deployment.

System projektu znaleziono znaki Unicode w niektórych właściwości na stronie właściwości wdrażania w Internecie, prawidłowo niemożliwymi do ANSI.

Rozwiązanie dotyczące tego błędu jest aktualizacji wartości właściwości, aby użyć ANSI lub Zainstaluj stronę kodową na swoim komputerze i jest ustawiony jako domyślny system.