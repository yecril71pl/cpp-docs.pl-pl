---
title: Klasy wyjątków
ms.date: 11/04/2016
f1_keywords:
- vc.classes.exception
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
ms.openlocfilehash: 907b34b12ffdaa70c4377a1012a66662fbba12d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619521"
---
# <a name="exception-classes"></a>Klasy wyjątków

Biblioteka klas zapewnia mechanizm obsługi wyjątków oparty na klasie `CException` . Struktura aplikacji używa wyjątków w kodzie. można ich również używać w swoich użytkownikach. Aby uzyskać więcej informacji, zobacz [wyjątki](exception-handling-in-mfc.md)w artykule. Możesz utworzyć własne typy wyjątków z `CException` .

MFC udostępnia klasę wyjątku, z której można utworzyć własny wyjątek, a także klasy wyjątków dla wszystkich obsługiwanych wyjątków.

[CException](reference/cexception-class.md)<br/>
Klasa bazowa dla wyjątków.

[CArchiveException](reference/carchiveexception-class.md)<br/>
Wyjątek archiwum.

[CDaoException](reference/cdaoexception-class.md)<br/>
Wyjątek wynikający z błędu w operacji bazy danych DAO.

[CDBException](reference/cdbexception-class.md)<br/>
Wyjątek wynikający z błędu podczas przetwarzania bazy danych ODBC.

[CFileException](reference/cfileexception-class.md)<br/>
Wyjątek zorientowany na pliki.

[CMemoryException](reference/cmemoryexception-class.md)<br/>
Wyjątek braku pamięci.

[CNotSupportedException](reference/cnotsupportedexception-class.md)<br/>
Wyjątek wynikający z użycia nieobsługiwanej funkcji.

[COleException](reference/coleexception-class.md)<br/>
Wyjątek wynikający z błędu przetwarzania OLE. Ta klasa jest używana przez kontenery i serwery.

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
Wyjątek wynikający z błędu podczas automatyzacji. Wyjątki automatyzacji są generowane przez serwery automatyzacji i przechwytywane przez klientów usługi Automation.

[CResourceException](reference/cresourceexception-class.md)<br/>
Wyjątek wynikający z niepowodzenia załadowania zasobu systemu Windows.

[CUserException](reference/cuserexception-class.md)<br/>
Wyjątek używany do zatrzymania operacji zainicjowanej przez użytkownika. Zazwyczaj użytkownik został powiadomiony o problemie przed zgłoszeniem tego wyjątku.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
