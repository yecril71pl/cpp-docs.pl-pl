---
title: Błąd PRJ0028 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0028
helpviewer_keywords:
- PRJ0028
ms.assetid: 0a6e0da7-cb3d-40b6-81a6-6196a9c2526b
ms.openlocfilehash: 9b74c64cee2b5734beab2bf30475b129160e67ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472842"
---
# <a name="project-build-error-prj0028"></a>Błąd PRJ0028 kompilacji projektu

Plik tymczasowy 'Plik' zawiera znaki unikodowe, które nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.

Określono wartość z [/MIDL (Określ opcje ze wiersza polecenia w MIDL)](../../build/reference/midl-specify-midl-command-line-options.md) opcji konsolidatora, która nie została rozpoznana przez stronę kodową systemu.

Strona kodowa używana podczas określania polecenia MIDL (wejściowej strony kodowej) musi być taka sama jak systemowa strona kodowa.