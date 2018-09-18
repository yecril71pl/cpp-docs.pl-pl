---
title: Błąd PRJ0008 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7c24634a845423de590228af01cb9f4779e37ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062790"
---
# <a name="project-build-error-prj0008"></a>Błąd PRJ0008 kompilacji projektu

Nie można usunąć pliku 'Plik'.

**Upewnij się, że plik nie jest otwarty przez inny proces i nie jest zabezpieczony przed zapisem.**

Podczas ponownej kompilacji lub czyszczenia, Visual C++ usuwa wszystkie znane plików pośrednich i wynikowych dla kompilacji, a także wszystkie pliki, które są zgodne ze specyfikacjami symbolu wieloznacznego w **rozszerzenia do usunięcia podczas oczyszczania** właściwość [ogólne Strona właściwości ustawień konfiguracji](../../ide/general-property-page-project.md).

Zostanie wyświetlony ten błąd, jeśli Visual C++ nie jest w stanie usunąć plik. Aby naprawić błąd, tworzenie pliku i jego katalogu zapisywalny dla użytkownika podczas kompilacji.