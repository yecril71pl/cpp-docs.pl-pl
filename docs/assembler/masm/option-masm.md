---
title: OPCJA (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09db749baf09525957faaf8af99434cc9775d0e7
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678048"
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
|**NOEMULATOR**|**EPILOGU**|**EXPR16**|**EXPR32**|
|**JĘZYK**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**PRZESUNIĘCIE**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGU**|**TYLKO DO ODCZYTU**|**NOREADONLY**|
|**O OKREŚLONYM ZAKRESIE**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|

Składnia języka jest **opcji języka:**<em>x</em>, gdzie *x* jest jednym z C, SYSCALL, STDCALL, PASCAL, PASCAL lub BASIC.  SYSCALL, PASCAL, PASCAL i BASIC są nieobsługiwane w przypadku używany z [. MODEL](../../assembler/masm/dot-model.md) PROSTEGO.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>