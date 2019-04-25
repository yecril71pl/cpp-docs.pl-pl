---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a8215bf1f816baa490a768fb2cab0b3c2e53e20b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217260"
---
# <a name="option-masm"></a>OPTION (MASM)

Włącza i wyłącza funkcje asembler.

## <a name="syntax"></a>Składnia

> Opcja *lista optionlist*

## <a name="remarks"></a>Uwagi

Dostępne opcje to:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULATOR**|
|**NOEMULATOR**|**EPILOGUE**|**EXPR16**|**EXPR32**|
|**JĘZYK**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**PRZESUNIĘCIE**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGU**|**TYLKO DO ODCZYTU**|**NOREADONLY**|
|**O OKREŚLONYM ZAKRESIE**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|

Składnia języka jest **opcji języka:**<em>x</em>, gdzie *x* jest jednym z C, SYSCALL, STDCALL, PASCAL, PASCAL lub BASIC.  SYSCALL, PASCAL, PASCAL i BASIC są nieobsługiwane w przypadku używany z [. MODEL](../../assembler/masm/dot-model.md) PROSTEGO.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>