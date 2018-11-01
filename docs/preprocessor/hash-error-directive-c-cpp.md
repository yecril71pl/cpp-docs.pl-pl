---
title: '#Błąd — dyrektywa (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: c83fc7ef8135ee0cba37a956df47bcab0f796007
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447817"
---
# <a name="error-directive-cc"></a>#error — dyrektywa (C/C++)
**#Error** dyrektywy emituje komunikat określony przez użytkownika w czasie kompilacji, a następnie kończy kompilacji.

## <a name="syntax"></a>Składnia

```
#errortoken-string
```

## <a name="remarks"></a>Uwagi

Zawiera komunikat o błędzie, który emituje ta dyrektywa *ciąg tokenu* parametru. *Ciąg tokenu* parametru nie podlega rozwinięciu makra. Ta dyrektywa jest najbardziej przydatna podczas przetwarzania wstępnego powiadamiania Deweloper niespójność program lub naruszenie ograniczenia. W poniższym przykładzie pokazano wystąpił błąd podczas przetwarzania podczas przetwarzania wstępnego:

```
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)