---
title: CColumnAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2a3b1dac51a8300a915a7177c36f15512b583fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212113"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor — Klasa

Generuje wstrzykiwany kod klienta.

## <a name="syntax"></a>Składnia

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Uwagi

W kodzie wstrzykiwanym każda kolumna jest powiązana jako oddzielna metoda dostępu. Należy pamiętać, że ta klasa jest używana w wstrzykiwanym kodzie (na przykład może wystąpić podczas debugowania), ale zazwyczaj nie trzeba używać jej bezpośrednio ani jej metod.

`CColumnAccessor` implementuje następujące metody zastępcze, z których każdy odpowiada w działaniu z innymi metodami klasy metody dostępu:

- `CColumnAccessor` konstruktora; tworzy wystąpienia i inicjuje obiekt `CColumnAccessor`.

- `CreateAccessor` przydziela pamięci dla struktur powiązań kolumn i inicjuje składowe danych kolumny.

- `BindColumns` wiąże kolumny z dostępem do metod dostępu.

- `SetParameterBuffer` przydziela bufory dla parametrów.

- `AddParameter` dodaje wpis parametru do struktur wpisów parametrów.

- `HasOutputColumns` określa, czy akcesor ma kolumny wyjściowe

- `HasParameters` określa, czy metoda dostępu ma parametry.

- `BindParameters` powiązania utworzonych parametrów z kolumnami.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)
