---
title: Inicjowanie i kończenie działania aparatu bazy danych DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: ccdf2e7b0f31576dddccad016e6b32806cdb82bf
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095880"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. 3,6 jest wersją ostateczną i jest uznawana za przestarzałą. W przypadku korzystania z obiektów MFC DAO aparat bazy danych DAO musi zostać najpierw zainicjowany, a następnie przerwany przed zakończeniem działania aplikacji lub biblioteki DLL. Dwie funkcje `AfxDaoInit` i `AfxDaoTerm`, wykonaj te zadania.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Inicjuje aparat bazy danych DAO.|
|[AfxDaoTerm](#afxdaoterm)|Kończy działanie aparatu bazy danych DAO.|

##  <a name="afxdaoinit"></a>AfxDaoInit

Ta funkcja inicjuje aparat bazy danych DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba wywoływać `AfxDaoInit` , ponieważ aplikacja automatycznie wywołuje ją, gdy jest potrzebna.

Aby uzyskać informacje pokrewne, a na przykład wywoływanie `AfxDaoInit`, zobacz [Uwagi techniczne 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

##  <a name="afxdaoterm"></a>AfxDaoTerm

Ta funkcja przerywa aparat bazy danych DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj należy wywołać tę funkcję tylko w zwykłej bibliotece MFC DLL; Aplikacja zostanie automatycznie wywołana `AfxDaoTerm` w razie konieczności.

W zwykłych bibliotekach DLL MFC `AfxDaoTerm` Wywołaj `ExitInstance` przed funkcją, ale po zniszczeniu wszystkich obiektów MFC DAO.

Aby uzyskać powiązane informacje, zobacz [Uwagi techniczne 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao. h

## <a name="see-also"></a>Zobacz także

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
