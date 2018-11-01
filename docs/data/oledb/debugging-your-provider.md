---
title: Debugowanie dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: e79719075bcd98733031abd63708bea861388cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466228"
---
# <a name="debugging-your-provider"></a>Debugowanie dostawcy

Istnieją dwa sposoby, aby debugować dostawcy:

- Ponieważ dostawców są tworzone w procesie, można utworzyć kodu odbiorcy zwykle za pomocą szablony konsumentów OLE DB i Wkrocz do dostawcy.

- Można użyć narzędzia ITEST, który jest dostarczany z programem Visual C++.

## <a name="to-use-the-itest-utility"></a>Aby korzystać z narzędzia ITEST

1. Otwórz projekt dostawcy.

1. Na **projektów** menu, kliknij przycisk **ustawienia**.

1. W **stron właściwości** okno dialogowe, kliknij przycisk **debugowania** kartę.

1. W **plik wykonywalny dla sesji debugowania** wybierz aplikacji ITEST.

1. Ustawianie punktów przerwania, a następnie debugować w zwykły sposób.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)