---
title: Funkcje ścieżki ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: 76efbb0bd43b800f186eac1afa168fc2a0c939f6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865038"
---
# <a name="atl-path-functions"></a>Funkcje ścieżki ATL

ATL udostępnia klasę ATLPath na potrzeby manipulowania ścieżkami w postaci [CPathT](cpatht-class.md). Ten kod można znaleźć w atlpath. h.

### <a name="related-classes"></a>Powiązane klasy

|||
|-|-|
|[Klasa CPathT](cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|

### <a name="related-typedefs"></a>Powiązane definicje typów

|||
|-|-|
|`CPath`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CString`.|
|`CPathA`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CStringA`.|
|`CPathW`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CStringW`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Ta funkcja to przeciążona otoka dla [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[ATLPath:: AddExtension](#addextension)|Ta funkcja to przeciążona otoka dla [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[ATLPath:: Append](#append)|Ta funkcja to przeciążona otoka dla [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[ATLPath:: element buildroot](#buildroot)|Ta funkcja to przeciążona otoka dla [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[ATLPath:: sprowadź](#canonicalize)|Ta funkcja to przeciążona otoka dla [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[ATLPath:: Połącz](#combine)|Ta funkcja to przeciążona otoka dla [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[ATLPath::CommonPrefix](#commonprefix)|Ta funkcja to przeciążona otoka dla [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[ATLPath::CompactPath](#compactpath)|Ta funkcja to przeciążona otoka dla [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[ATLPath::CompactPathEx](#compactpathex)|Ta funkcja to przeciążona otoka dla [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[ATLPath::FileExists](#fileexists)|Ta funkcja to przeciążona otoka dla [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[ATLPath::FindExtension](#findextension)|Ta funkcja to przeciążona otoka dla [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[ATLPath::FindFileName](#findfilename)|Ta funkcja to przeciążona otoka dla [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Ta funkcja to przeciążona otoka dla [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[ATLPath:: IsDirectory](#isdirectory)|Ta funkcja to przeciążona otoka dla [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[ATLPath::IsFileSpec](#isfilespec)|Ta funkcja to przeciążona otoka dla [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[ATLPath:: IsPrefix](#isprefix)|Ta funkcja to przeciążona otoka dla [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).|
|[ATLPath:: isrelatywn](#isrelative)|Ta funkcja to przeciążona otoka dla [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[ATLPath:: IsRoot](#isroot)|Ta funkcja to przeciążona otoka dla [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[ATLPath::IsSameRoot](#issameroot)|Ta funkcja to przeciążona otoka dla [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).|
|[ATLPath::IsUNC](#isunc)|Ta funkcja to przeciążona otoka dla [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[ATLPath::IsUNCServer](#isuncserver)|Ta funkcja to przeciążona otoka dla [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Ta funkcja to przeciążona otoka dla [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[ATLPath::MakePretty](#makepretty)|Ta funkcja to przeciążona otoka dla [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[ATLPath::MatchSpec](#matchspec)|Ta funkcja to przeciążona otoka dla [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[ATLPath::QuoteSpaces](#quotespaces)|Ta funkcja to przeciążona otoka dla [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[ATLPath::RelativePathTo](#relativepathto)|Ta funkcja to przeciążona otoka dla [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[ATLPath::RemoveArgs](#removeargs)|Ta funkcja to przeciążona otoka dla [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).|
|[ATLPath::RemoveBackslash](#removebackslash)|Ta funkcja to przeciążona otoka dla [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).|
|[ATLPath::RemoveBlanks](#removeblanks)|Ta funkcja to przeciążona otoka dla [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).|
|[ATLPath::RemoveExtension](#removeextension)|Ta funkcja to przeciążona otoka dla [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Ta funkcja to przeciążona otoka dla [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).|
|[ATLPath::RenameExtension](#renameextension)|Ta funkcja to przeciążona otoka dla [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[ATLPath::SkipRoot](#skiproot)|Ta funkcja to przeciążona otoka dla [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[ATLPath::StripPath](#strippath)|Ta funkcja to przeciążona otoka dla [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[ATLPath::StripToRoot](#striptoroot)|Ta funkcja to przeciążona otoka dla [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Ta funkcja to przeciążona otoka dla [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath. h

## <a name="addbackslash"></a>ATLPath::AddBackSlash

Ta funkcja to przeciążona otoka dla [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Składnia

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) .

## <a name="addextension"></a>ATLPath:: AddExtension

Ta funkcja to przeciążona otoka dla [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Składnia

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) .

## <a name="append"></a>ATLPath:: Append

Ta funkcja to przeciążona otoka dla [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Składnia

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) .

## <a name="buildroot"></a>ATLPath:: element buildroot

Ta funkcja to przeciążona otoka dla [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Składnia

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) .

## <a name="canonicalize"></a>ATLPath:: sprowadź

Ta funkcja to przeciążona otoka dla [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Składnia

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) .

## <a name="combine"></a>ATLPath:: Połącz

Ta funkcja to przeciążona otoka dla [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

### <a name="syntax"></a>Składnia

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz PathCombine.

## <a name="commonprefix"></a>ATLPath::CommonPrefix

Ta funkcja to przeciążona otoka dla [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

### <a name="syntax"></a>Składnia

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) .

## <a name="compactpath"></a>ATLPath::CompactPath

Ta funkcja to przeciążona otoka dla [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

### <a name="syntax"></a>Składnia

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) .

## <a name="compactpathex"></a>ATLPath::CompactPathEx

Ta funkcja to przeciążona otoka dla [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

### <a name="syntax"></a>Składnia

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) .

## <a name="fileexists"></a>ATLPath::FileExists

Ta funkcja to przeciążona otoka dla [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Składnia

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) .

## <a name="findextension"></a>ATLPath::FindExtension

Ta funkcja to przeciążona otoka dla [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Składnia

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) .

## <a name="findfilename"></a>ATLPath::FindFileName

Ta funkcja to przeciążona otoka dla [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Składnia

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) .

## <a name="getdrivenumber"></a>ATLPath::GetDriveNumber

Ta funkcja to przeciążona otoka dla [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Składnia

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) .

## <a name="isdirectory"></a>ATLPath:: IsDirectory

Ta funkcja to przeciążona otoka dla [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz PathIsDirectory.

## <a name="isfilespec"></a>ATLPath::IsFileSpec

Ta funkcja to przeciążona otoka dla [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) .

## <a name="isprefix"></a>ATLPath:: IsPrefix

Ta funkcja to przeciążona otoka dla [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) .

## <a name="isrelative"></a>ATLPath:: isrelatywn

Ta funkcja to przeciążona otoka dla [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Składnia

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) .

## <a name="isroot"></a>ATLPath:: IsRoot

Ta funkcja to przeciążona otoka dla [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) .

## <a name="issameroot"></a>ATLPath::IsSameRoot

Ta funkcja to przeciążona otoka dla [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) .

## <a name="isunc"></a>ATLPath::IsUNC

Ta funkcja to przeciążona otoka dla [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) .

## <a name="isuncserver"></a>ATLPath::IsUNCServer

Ta funkcja to przeciążona otoka dla [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) .

## <a name="isuncservershare"></a>ATLPath::IsUNCServerShare

Ta funkcja to przeciążona otoka dla [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) .

## <a name="makepretty"></a>ATLPath::MakePretty

Ta funkcja to przeciążona otoka dla [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Składnia

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) .

## <a name="matchspec"></a>ATLPath::MatchSpec

Ta funkcja to przeciążona otoka dla [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Składnia

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) .

## <a name="quotespaces"></a>ATLPath::QuoteSpaces

Ta funkcja to przeciążona otoka dla [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Składnia

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) .

## <a name="relativepathto"></a>ATLPath::RelativePathTo

Ta funkcja to przeciążona otoka dla [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

### <a name="syntax"></a>Składnia

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) .

## <a name="removeargs"></a>ATLPath::RemoveArgs

Ta funkcja to przeciążona otoka dla [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

### <a name="syntax"></a>Składnia

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) .

## <a name="removebackslash"></a>ATLPath::RemoveBackslash

Ta funkcja to przeciążona otoka dla [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

### <a name="syntax"></a>Składnia

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) .

## <a name="removeblanks"></a>ATLPath::RemoveBlanks

Ta funkcja to przeciążona otoka dla [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

### <a name="syntax"></a>Składnia

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) .

## <a name="removeextension"></a>ATLPath::RemoveExtension

Ta funkcja to przeciążona otoka dla [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

### <a name="syntax"></a>Składnia

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) .

## <a name="removefilespec"></a>ATLPath::RemoveFileSpec

Ta funkcja to przeciążona otoka dla [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

### <a name="syntax"></a>Składnia

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) .

## <a name="renameextension"></a>ATLPath::RenameExtension

Ta funkcja to przeciążona otoka dla [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Składnia

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) .

## <a name="skiproot"></a>ATLPath::SkipRoot

Ta funkcja to przeciążona otoka dla [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Składnia

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) .

## <a name="strippath"></a>ATLPath::StripPath

Ta funkcja to przeciążona otoka dla [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Składnia

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) .

## <a name="striptoroot"></a>ATLPath::StripToRoot

Ta funkcja to przeciążona otoka dla [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Składnia

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) .

## <a name="unquotespaces"></a>ATLPath::UnquoteSpaces

Ta funkcja to przeciążona otoka dla [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Składnia

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Aby uzyskać szczegółowe informacje, zobacz [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) .
