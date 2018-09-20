---
title: Klasa CUserException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71d2be1c00e518597a5d5121d7a53544bd29067f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419662"
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

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)
