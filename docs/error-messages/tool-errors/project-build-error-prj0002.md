---
title: Błąd PRJ0002 kompilacji projektu
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: 30680f5b26f3be5e7f9b48d18e82fca42ed65493
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192942"
---
# <a name="project-build-error-prj0002"></a>Błąd PRJ0002 kompilacji projektu

> wynik błędu zwrócony z "*wiersz polecenia*".

Polecenie, *wiersz polecenia*, który został utworzony na podstawie danych wejściowych użytkownika w oknie dialogowym **strony właściwości** , zwróciło kod błędu, ale w oknie **danych wyjściowych** nie będą wyświetlane żadne informacje.

Rozwiązanie tego błędu zależy od tego, który narzędzie wygenerowało błąd. W przypadku MIDL uzyskasz informacje o tym, co poszło źle, jeśli są zdefiniowane/o (dane wyjściowe przekierowania).

Przyczyną tego błędu może być plik wsadowy, taki jak niestandardowy krok kompilacji lub zdarzenie kompilacji, które nie opisują warunków błędu.
