---
title: '@ (Określ plik odpowiedzi kompilatora)'
ms.date: 11/04/2016
f1_keywords:
- '@'
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
ms.openlocfilehash: 90dcadbb47cdc7eb4fa1ff039f5074a3141eac83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491315"
---
# <a name="-specify-a-compiler-response-file"></a>@ (Określ plik odpowiedzi kompilatora)

Określa plik odpowiedzi kompilatora.

## <a name="syntax"></a>Składnia

> **\@**<em>response_file</em>

## <a name="arguments"></a>Argumenty

*response_file*<br/>
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

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
