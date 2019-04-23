---
title: Redystrybucja składników ODBC wśród klientów
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: 1a6ec6f5fdd3c32080d357ca58d31ccea271b7a4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040098"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redystrybucja składników ODBC wśród klientów

Jeśli funkcje programów ODBC Administrator jest uwzględnienie w aplikacji, musisz również przeprowadzić dystrybucję użytkownikom pliki, które uruchamiania tych programów. Te pliki ODBC znajdują się w katalogu \OS\System dysk CD z Visual C++. Plik Redistrb.wri i umowę licencyjną, w tym samym katalogu zawiera listę plików ODBC, które można redystrybuować.

Zajrzyj do dokumentacji dla wszystkich sterowników ODBC, który będzie dostarczany. Należy określić, które biblioteki dll i inne pliki do wysłania. Należy również przeczytać [Redystrybucja składników ODBC wśród klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md), która wyjaśnia, jak Redystrybucja składników ODBC.

Ponadto konieczne jest uwzględnienie jednego pliku w większości przypadków. Odbccr32.dll jest z biblioteki kursorów ODBC. Ta biblioteka zapewnia sterowniki 1 poziom możliwości przewijanie do przodu i Wstecz. Zapewnia również możliwość obsługi migawek. Aby uzyskać więcej informacji na temat z biblioteki kursorów ODBC, zobacz [ODBC: ODBC — Biblioteka kursorów](../../data/odbc/odbc-the-odbc-cursor-library.md).

Więcej informacji o używaniu ODBC z klasami bazy danych można znaleźć w następujących tematach:

- [ODBC: Z biblioteki kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: Konfigurowanie źródła danych ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: Bezpośrednie wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Zobacz także

[Podstawy ODBC](../../data/odbc/odbc-basics.md)<br/>
[Administrator ODBC](../../data/odbc/odbc-administrator.md)