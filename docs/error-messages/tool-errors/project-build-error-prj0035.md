---
title: Błąd PRJ0035 kompilacji projektu
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: 8486c4f62f637f6f7e9826a289c21f8f194eb9f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192177"
---
# <a name="project-build-error-prj0035"></a>Błąd PRJ0035 kompilacji projektu

> Plik XML "*File*" zawiera zawartość Unicode, której nie można przetłumaczyć na stronę kodową ANSI użytkownika.
>
> *Zawartość UNICODE pliku*

*plik* to plik XML utworzony jako wiersz polecenia narzędzia Web Deployment.

System projektu znalazł znaki Unicode w pewnej właściwości na stronie właściwości wdrożenia sieci Web, które nie mogą być prawidłowo tłumaczone na ANSI.

Rozwiązaniem tego błędu jest aktualizacja zawartości właściwości w celu użycia ANSI lub zainstalowania strony kodowej na komputerze i ustawienie jej jako wartości domyślnej systemu.
