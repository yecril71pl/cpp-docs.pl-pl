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
ms.openlocfilehash: dc229a8eae6938cba32787ecbec6a5aa6a17ab47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383989"
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

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)