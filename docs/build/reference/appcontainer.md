---
title: /APPCONTAINER
ms.date: 11/04/2016
f1_keywords:
- /APPCONTAINER
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
ms.openlocfilehash: 0805393990070a10caed8208138e31ab9084bdf0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482557"
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