---
title: '#error, dyrektywa (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: bfb5c18f20319e6e6d345f28d3e1850714334b71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216120"
---
# <a name="error-directive-cc"></a>#error — dyrektywa (CC++/)

Dyrektywa **#error** emituje określony przez użytkownika komunikat o błędzie w czasie kompilacji, a następnie kończy kompilację.

## <a name="syntax"></a>Składnia

> **#error** *token — ciąg*

## <a name="remarks"></a>Uwagi

Komunikat o błędzie, który jest emitowany przez tę dyrektywę, zawiera parametr *token-String* . Parametr *tokenu-String* nie podlega rozszerzeniu makra. Ta dyrektywa jest najbardziej przydatna podczas przetwarzania wstępnego, w celu powiadomienia dewelopera niespójności programu lub naruszenia ograniczenia. Poniższy przykład ilustruje przetwarzanie błędów podczas przetwarzania wstępnego:

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)
