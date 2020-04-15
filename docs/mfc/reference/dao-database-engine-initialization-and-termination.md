---
title: Inicjowanie i kończenie działania aparatu bazy danych DAO
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 62460e8e55f70b8cb0743f1d044636d25121050d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365891"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

DAO jest używany z bazami danych programu Access i jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą. Podczas korzystania z obiektów DAO MFC aparat bazy danych DAO musi najpierw zostać zainicjowany, a następnie zakończony przed zamknięciem aplikacji lub biblioteki DLL. Dwie `AfxDaoInit` funkcje `AfxDaoTerm`i , wykonaj te zadania.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

|||
|-|-|
|[AfxDaoInit ( AfxDaoInit )](#afxdaoinit)|Inicjuje aparat bazy danych DAO.|
|[AfxDaoTerm (AfxDaoTerm)](#afxdaoterm)|Kończy aparat bazy danych DAO.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a>AfxDaoInit ( AfxDaoInit )

Ta funkcja inicjuje aparat bazy danych DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba dzwonić, `AfxDaoInit` ponieważ aplikacja automatycznie wywołuje go, gdy jest to potrzebne.

Informacje pokrewne oraz przykład `AfxDaoInit`połączenia telefonicznego można znaleźć [w notatce technicznej 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a>AfxDaoTerm (AfxDaoTerm)

Ta funkcja powoduje zakończenie aparatu bazy danych DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Uwagi

Zazwyczaj wystarczy wywołać tę funkcję tylko w zwykłej biblioteki DLL MFC; aplikacja automatycznie zadzwoni, `AfxDaoTerm` gdy będzie potrzebna.

W zwykłych bibliotekach DLL MFC wywołaj `AfxDaoTerm` przed funkcją, `ExitInstance` ale po zniszczeniu wszystkich obiektów DAO MFC.

Aby uzyskać powiązane informacje, zobacz [uwaga techniczna 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
