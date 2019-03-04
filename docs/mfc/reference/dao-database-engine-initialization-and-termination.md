---
title: Inicjowanie i kończenie działania aparatu bazy danych DAO
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.data
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 8ad0c1df2f5b6a7b1b48d2db119b04e4b3234f10
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297644"
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
