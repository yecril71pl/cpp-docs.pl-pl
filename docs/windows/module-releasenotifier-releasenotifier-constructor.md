---
title: 'Module::releasenotifier:: releasenotifier, Konstruktor | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e43abd46ccfb150936ff435360611289f18a1270
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405024"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier — Konstruktor

Inicjuje nowe wystąpienie klasy **Module::ReleaseNotifier** klasy.

## <a name="syntax"></a>Składnia

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*Wydania*<br/>
**wartość true,** można usunąć to wystąpienie kiedy `Release` wywoływana jest metoda; **false** nie należy usuwać tego wystąpienia.

## <a name="exceptions"></a>Wyjątki

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Module::ReleaseNotifier, klasa](../windows/module-releasenotifier-class.md)