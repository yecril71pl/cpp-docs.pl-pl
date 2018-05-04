---
title: Abort — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/01/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4acfbb5a0790dec6f7b5770832cc6b09f69a28d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="abort-function"></a>abort — funkcja

**Przerwać** funkcji również zadeklarowany w pliku dołączanego standardowe \<stdlib.h >, program w języku C++ kończy. Różnica między **zakończyć** i **przerwać** jest to, że **zakończyć** pozwala na przetwarzanie zakończenia środowiska wykonawczego języka C++ została wykonana (globalny obiekt będzie można wywołać destruktorów), podczas gdy **przerwać** natychmiast kończy program. Aby uzyskać więcej informacji, zobacz [przerwać](../c-runtime-library/reference/abort.md) w *odwołanie do biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz także

[Kończenie działania programu](../cpp/program-termination.md)