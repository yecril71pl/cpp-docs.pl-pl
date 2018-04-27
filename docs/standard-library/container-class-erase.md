---
title: Kontener Class::erase | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d5a817ed259f5bd264d82fc948afa4cdcd70be2e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="container-classerase"></a>Kontener Class::erase

> [!NOTE]
> Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).

Usuwa element.

## <a name="syntax"></a>Składnia

```

    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Uwagi

Pierwszy funkcji członkowskiej spowoduje usunięcie elementu w kontrolowanej sekwencji wskazywana przez *_Where*. Drugi funkcji członkowskiej usuwa elementy kontrolowanej sekwencji z zakresu [`first`, `last`). Obie zwracają iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub [zakończenia](../standard-library/container-class-end.md) Jeżeli nie zawiera żadnego takiego elementu.

Funkcje Członkowskie Zgłoś wyjątek, tylko wtedy, gdy operacja kopiowania zgłasza wyjątek.

## <a name="see-also"></a>Zobacz także

[Sample Container, klasa](../standard-library/sample-container-class.md)<br/>
