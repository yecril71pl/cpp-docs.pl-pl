---
title: Redystrybucja składników ODBC wśród klientów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b28d743b933caab5a017d89b636a78fd8890c10
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069493"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redystrybucja składników ODBC wśród klientów

Jeśli funkcje programów ODBC Administrator jest uwzględnienie w aplikacji, musisz również przeprowadzić dystrybucję użytkownikom pliki, które uruchamiania tych programów. Te pliki ODBC znajdują się w katalogu \OS\System dysk CD z Visual C++. Plik Redistrb.wri i umowę licencyjną, w tym samym katalogu zawiera listę plików ODBC, które można redystrybuować.

Zajrzyj do dokumentacji dla wszystkich sterowników ODBC, który będzie dostarczany. Należy określić, które biblioteki dll i inne pliki do wysłania. Należy również przeczytać [Redystrybucja składników ODBC wśród klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md), która wyjaśnia, jak Redystrybucja składników ODBC.

Ponadto konieczne jest uwzględnienie jednego pliku w większości przypadków. Odbccr32.dll jest z biblioteki kursorów ODBC. Ta biblioteka zapewnia sterowniki 1 poziom możliwości przewijanie do przodu i Wstecz. Zapewnia również możliwość obsługi migawek. Aby uzyskać więcej informacji na temat z biblioteki kursorów ODBC, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

Więcej informacji o używaniu ODBC z klasami bazy danych można znaleźć w następujących tematach:

- [ODBC: biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: konfigurowanie źródła danych ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: bezpośrednie wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)<br/>
[Administrator ODBC](../../data/odbc/odbc-administrator.md)