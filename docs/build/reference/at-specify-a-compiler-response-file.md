---
title: '@ (Określ plik odpowiedzi kompilatora) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 430e6372c1ca26e946c2ff26bfcfe9180dfb0dba
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894463"
---
# <a name="-specify-a-compiler-response-file"></a>@ (Określ plik odpowiedzi kompilatora)

Określa plik odpowiedzi kompilatora.

## <a name="syntax"></a>Składnia

> **\@**<em>response_file</em>

## <a name="arguments"></a>Argumenty

*response_file*  
Plik tekstowy zawierający polecenia kompilatora.

## <a name="remarks"></a>Uwagi

Plik odpowiedzi może zawierać dowolne polecenia, które należy określić w wierszu polecenia. Może to być przydatne, jeśli argumenty wiersza poleceń przekracza 127 znaków.

Nie jest możliwe do określenia **\@** opcję w pliku odpowiedzi. Oznacza to, że plik odpowiedzi nie można osadzić inny plik odpowiedzi.

W wierszu polecenia można określić dowolną liczbę opcji pliku odpowiedzi (na przykład `@respfile.1 @respfile.2`) jak chcesz.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

- Plik odpowiedzi nie można określić w środowisku programistycznym, a musi być określona w wierszu polecenia.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Nie można programowo zmienić tę opcję kompilatora.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
