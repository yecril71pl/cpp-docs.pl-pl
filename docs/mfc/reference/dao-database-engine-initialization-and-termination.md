---
title: Inicjowanie i kończenie działania aparatu bazy danych DAO
ms.date: 11/04/2016
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 1b8186627f00105cf782586060b41ae0fb627d76
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611935"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

Korzystając z obiektów MFC DAO, aparat bazy danych DAO muszą najpierw być zainicjowane, a następnie zakończone przed kończy działanie aplikacji lub biblioteki DLL. Dwie funkcje `AfxDaoInit` i `AfxDaoTerm`, wykonywania tych zadań.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|Inicjuje aparat bazy danych DAO.|
|[AfxDaoTerm](#afxdaoterm)|Kończy się z aparatem bazy danych DAO.|

##  <a name="afxdaoinit"></a>  AfxDaoInit

Ta funkcja inicjuje aparat bazy danych DAO.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba wywoływać `AfxDaoInit` ponieważ aplikacja automatycznie wywołuje on kiedy jest potrzebny.

Aby uzyskać powiązane informacje i przykład wywołania metody `AfxDaoInit`, zobacz [techniczne 54 Uwaga](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

Ta funkcja kończy się z aparatem bazy danych DAO.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>Uwagi

Zwykle wystarczy wywołać tę funkcję w zwykłej biblioteki MFC DLL; aplikacja będzie automatycznie wywoływać `AfxDaoTerm` kiedy jest potrzebny.

W zwykłych bibliotekach MFC dll, należy wywołać `AfxDaoTerm` przed `ExitInstance` funkcji, ale po zniszczeniu wszystkich obiektów MFC DAO.

Aby uzyskać powiązane informacje, zobacz [techniczne 54 Uwaga](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdao.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
