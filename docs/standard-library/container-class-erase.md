---
title: Kontener Class::erase | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 368b722f03a68445ddd016705aa8bebc6f33e6f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
