---
title: Debugowanie dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59431204ae242ac6fab0d562740f859dc85bcd11
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081800"
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