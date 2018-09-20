---
title: Inicjowanie aparatu bazy danych DAO i kończenie działania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf54992896559f1b143247746ef9f9e0e8d8979
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404010"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

Korzystając z obiektów MFC DAO, aparat bazy danych DAO muszą najpierw być zainicjowane, a następnie zakończone przed kończy działanie aplikacji lub biblioteki DLL. Dwie funkcje `AfxDaoInit` i `AfxDaoTerm`, wykonywania tych zadań.

### <a name="dao-database-engine-initialization-and-termination"></a>Inicjowanie i kończenie działania aparatu bazy danych DAO

|||
|-|-|
|[Afxdaoinit —](#afxdaoinit)|Inicjuje aparat bazy danych DAO.|
|[Afxdaoterm —](#afxdaoterm)|Kończy się z aparatem bazy danych DAO.|

##  <a name="afxdaoinit"></a>  Afxdaoinit —

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

##  <a name="afxdaoterm"></a>  Afxdaoterm —

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

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
