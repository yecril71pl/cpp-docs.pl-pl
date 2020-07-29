---
title: BufferCommand, Wyliczenie
description: 'Opisuje Wyliczenie BufferCommand, które jest używane do pracy z plikami pamięci za pośrednictwem CMemFile:: GetBufferPtr ()'
ms.date: 07/23/2020
f1_keywords:
- afx/buffercommand
helpviewer_keywords:
- buffercommand enumeration [MFC]
ms.openlocfilehash: f2f553df56fadd99b65b04cce9a97917425ed70b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87246119"
---
# <a name="buffercommand-enumeration"></a>BufferCommand, Wyliczenie

Używane przez [CMemFile:: GetBufferPtr](cmemfile-class.md#getbufferptr) w celu określenia działania, które należy wykonać w buforze pamięci z kopią zapasową w pliku.

## <a name="syntax"></a>Składnia

``` cpp
public enum BufferCommand
{
   bufferRead,
   bufferWrite,
   bufferCommit,
   bufferCheck
};
```

## <a name="members"></a>Elementy członkowskie

|Nazwa|Opis|
|-|-|
| `bufferRead` | Odczytaj bufor pamięci z kopią zapasową w pliku. |
| `bufferWrite` | Zapisz w buforze pamięci z kopią zapasową w pliku. |
| `bufferCommit` | Zwiększa aktualną pozycję w buforze pamięci z kopią zapasową w pliku na końcu przekazanego buforu. |
| `bufferCheck` | Ustal, czy rozmiar buforu pamięci, który można zwiększyć, jest większy. |

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)
