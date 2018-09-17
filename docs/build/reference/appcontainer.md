---
title: -APPCONTAINER | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d8e19724183963329b959286a996b4f21d18b4c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709186"
---
# <a name="appcontainer"></a>/APPCONTAINER

Oznacza plik wykonywalny, który należy uruchomić w pojemniku aplikacji — na przykład aplikacji Microsoft Store lub Universal Windows.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Uwagi

Plik wykonywalny, który ma **/appcontainer** zestaw opcji może być uruchamiany tylko w pojemniku aplikacji, który jest środowiskiem izolacja procesu, wprowadzona w systemie Windows 8. W przypadku aplikacji Microsoft Store i Windows Universal można ustawić tę opcję.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)<br/>
[Co to jest aplikacją Universal Windows?](/windows/uwp/get-started/universal-application-platform-guide)