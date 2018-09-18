---
title: Błąd PRJ0028 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0028
dev_langs:
- C++
helpviewer_keywords:
- PRJ0028
ms.assetid: 0a6e0da7-cb3d-40b6-81a6-6196a9c2526b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f90e7f6629ae50f734ac127d05c6c70d002133a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062621"
---
# <a name="project-build-error-prj0028"></a>Błąd PRJ0028 kompilacji projektu

Plik tymczasowy 'Plik' zawiera znaki unikodowe, które nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.

Określono wartość z [/MIDL (Określ opcje ze wiersza polecenia w MIDL)](../../build/reference/midl-specify-midl-command-line-options.md) opcji konsolidatora, która nie została rozpoznana przez stronę kodową systemu.

Strona kodowa używana podczas określania polecenia MIDL (wejściowej strony kodowej) musi być taka sama jak systemowa strona kodowa.