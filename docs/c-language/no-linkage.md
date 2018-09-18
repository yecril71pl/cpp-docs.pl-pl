---
title: Brak połączenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acbce1b4a4a19c5fa1a015e01bd2078fc70f6e1c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063089"
---
# <a name="no-linkage"></a>Brak połączenia

Jeśli nie ma deklarację dla identyfikatora w bloku `extern` Specyfikator klasy magazynowania, identyfikator ma bez połączenia i jest unikatowy dla funkcji.

Następujące identyfikatory są bez połączenia:

- Identyfikator zadeklarowany za nic innego niż obiekt lub funkcja

- Identyfikator zadeklarowany jako parametr funkcji

- Identyfikator o zakresie bloku dla obiektu zadeklarowana bez `extern` Specyfikator klasy magazynowania

Jeśli identyfikator ma bez połączenia, Zadeklarowanie tej samej nazwie ponownie (w deklarator lub Specyfikator typu), w tym samym poziomie zakresu generuje błąd zmiana definicji symbolu.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)