---
title: Klasa CUserException
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 72d8537616792859a2b00a1a5cd880ce5eb452bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323440"
---
# <a name="cuserexception-class"></a>Klasa CUserException

Element zgłaszany, aby zatrzymać operacje użytkownika końcowego.

## <a name="syntax"></a>Składnia

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>Uwagi

Użyj `CUserException` gdy zachodzi potrzeba użycia mechanizm wyjątków throw/catch do obsługi wyjątków specyficzne dla aplikacji. "Użytkownik" w nazwie klasy mogą być interpretowane jako "Moje użytkownika zrobił coś wyjątkowe, potrzebne do obsługi".

A `CUserException` jest zazwyczaj zgłaszany po wywołaniu funkcji globalnej `AfxMessageBox` do powiadamiania użytkownika, że operacja zakończyła się niepowodzeniem. Pisząc program obsługi wyjątku obsłużyć wyjątek, specjalnie, ponieważ użytkownik zwykle już zgłoszono błędu. Struktura zgłasza ten wyjątek w niektórych przypadkach. Aby zgłosić `CUserException` samodzielnie, ostrzegać użytkowników, a następnie wywołać funkcję globalnego `AfxThrowUserException`.

W poniższym przykładzie funkcja zawierająca operacje, które może się nie powieść ostrzega o tym użytkownika i zgłasza `CUserException`. Funkcja wywołująca przechwytuje wyjątek i obsługuje je specjalnie:

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

Aby uzyskać więcej informacji na temat korzystania z `CUserException`, zapoznaj się z artykułem [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
