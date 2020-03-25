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
ms.openlocfilehash: 0d4d3948add665c54be3d3b0596a7a6fc0e414f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212735"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redystrybucja składników ODBC wśród klientów

Jeśli dołączysz funkcjonalność programów administratora ODBC do aplikacji, musisz również przekazać użytkownikom pliki, które uruchamiają te programy. Te pliki ODBC znajdują się w katalogu \OS\System w Visual C++ CD-ROM. Plik Redistrb. wri i Umowa licencyjna w tym samym katalogu zawierają listę plików ODBC, które można rozpowszechniać.

Zapoznaj się z dokumentacją dotyczącą wszelkich sterowników ODBC, które planujesz wysłać. Należy określić, które biblioteki DLL i inne pliki mają być dostarczane. Należy również zapoznać [się z redystrybucją składników ODBC do klientów](../../data/odbc/redistributing-odbc-components-to-your-customers.md), co wyjaśnia, jak ponownie dystrybuować składniki ODBC.

Ponadto należy w większości przypadków dołączyć jeden plik. Odbccr32. dll jest biblioteką kursora ODBC. Ta biblioteka zapewnia poziom 1 Sterowniki możliwości przewijania do przodu i do tyłu. Oferuje również możliwość obsługi migawek. Aby uzyskać więcej informacji na temat biblioteki kursora ODBC, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

Poniższe tematy zawierają więcej informacji na temat używania ODBC z klasami baz danych:

- [ODBC: biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: konfigurowanie źródła danych ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: bezpośrednie wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)<br/>
[Administrator ODBC](../../data/odbc/odbc-administrator.md)
