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
ms.openlocfilehash: fad88fa36c64bd9d8ca28135c09a3f0ce8fe3c0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441941"
---
# <a name="exception-classes"></a>Klasy wyjątków

Biblioteka klas udostępnia mechanizm obsługi wyjątków, na podstawie klasy `CException`. Struktura aplikacji używa wyjątków w jego kod; Umożliwia także je w należy do Ciebie. Aby uzyskać więcej informacji, zobacz artykuł [wyjątki](../mfc/exception-handling-in-mfc.md). Uzyskujesz własnych typów wyjątków z `CException`.

Biblioteka MFC zawiera klasę wyjątku, z którego można uzyskać własne wyjątek, a także klasy wyjątków dla wszystkich wyjątków, który ją obsługuje.

[CException](../mfc/reference/cexception-class.md)<br/>
Klasa bazowa dla wyjątków.

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
Wyjątek archiwum.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Wyjątek, wynikające z wystąpił błąd podczas operacji bazy danych DAO.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Wyjątek, wynikające z wystąpił błąd podczas przetwarzania baz danych ODBC.

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
Wyjątek zorientowane na plik.

[CMemoryException](../mfc/reference/cmemoryexception-class.md)<br/>
Wyjątek braku pamięci.

[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)<br/>
Wyjątek, wynikające z używa nieobsługiwanej funkcji.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Wyjątek, wynikające z wystąpił błąd podczas przetwarzania OLE. Ta klasa jest używana zarówno kontenery i serwery.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Wyjątek wynikającego z błędem podczas automatyzacji. Automation wyjątki są zgłaszane przez serwery automatyzacji i przechwycony przez klientów automatyzacji.

[CResourceException](../mfc/reference/cresourceexception-class.md)<br/>
Wyjątek podczas awarii można załadować zasobu Windows.

[CUserException](../mfc/reference/cuserexception-class.md)<br/>
Wyjątek umożliwia zatrzymać operację Zainicjowanie przez użytkownika. Zazwyczaj użytkownik został powiadomiony o problem zanim ten wyjątek.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

