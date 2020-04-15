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
ms.openlocfilehash: f3d8fa63e7fd20f8a0d6759fee8417b3fbc29486
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319222"
---
# <a name="atl-path-functions"></a>Funkcje ścieżki ATL

ATL udostępnia klasę ATLPath do manipulowania ścieżkami w postaci [CPathT](cpatht-class.md). Ten kod można znaleźć w atlpath.h.

### <a name="related-classes"></a>Powiązane klasy

|||
|-|-|
|[Klasa CPatht](cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|

### <a name="related-typedefs"></a>Powiązane typedefs

|||
|-|-|
|`CPath`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CString`.|
|`CPathA`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CStringA`.|
|`CPathW`|Specjalizacja [CPathT](cpatht-class.md) przy użyciu `CStringW`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Ta funkcja jest przeciążonym otoką dla [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[ATLPath::AddExtension](#addextension)|Ta funkcja jest przeciążonym otoką [pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[ATLPath::Dołącz](#append)|Ta funkcja jest przeciążonym otoką [pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[ATLPath::BuildRoot](#buildroot)|Ta funkcja jest przeciążonym otoką [pathbuildroot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[ATLPath::Canonicalize](#canonicalize)|Ta funkcja jest przeciążonym otoką [pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[ATLPath::Kombajn](#combine)|Ta funkcja jest przeciążonym otoką [pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[ATLPath::CommonPrefix](#commonprefix)|Ta funkcja jest przeciążonym otokiem [pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[ATLPath::CompactPath](#compactpath)|Ta funkcja jest przeciążonym otoką [pathcompactpath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[ATLPath::CompactPathEx](#compactpathex)|Ta funkcja jest przeciążonym otoką [pathcompactpathex](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[ATLPath::FileExists](#fileexists)|Ta funkcja jest przeciążonym otoką [pathfileexists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[ATLPath::FindExtension](#findextension)|Ta funkcja jest przeciążonym otoką [pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[ATLPath::FindFileName](#findfilename)|Ta funkcja jest przeciążonym otoką [pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Ta funkcja jest przeciążonym otoką dla [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[ATLPath::IsDirectory](#isdirectory)|Ta funkcja jest przeciążonym otoką [pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[ATLPath::IsFileSpec](#isfilespec)|Ta funkcja jest przeciążonym otoką [pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[ATLPath::IsPrefix](#isprefix)|Ta funkcja jest przeciążonym otokiem [pathisprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).|
|[ATLPath::IsRelative](#isrelative)|Ta funkcja jest przeciążonym otokiem [pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[ATLPath::IsRoot](#isroot)|Ta funkcja jest przeciążonym otoką [pathisroot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[ATLPath::IsSameRoot](#issameroot)|Ta funkcja jest przeciążonym otoką [pathisSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).|
|[ATLPath::IsUNC](#isunc)|Ta funkcja jest przeciążonym otoką [pathisUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[ATLPath::Serwer ISUNCServer](#isuncserver)|Ta funkcja jest przeciążonym otoką [pathisUncserver](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Ta funkcja jest przeciążonym otoką [pathisUncservershare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[ATLPath::MakePretty](#makepretty)|Ta funkcja jest przeciążonym otokiem [pathmakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[ATLPath::MatchSpec](#matchspec)|Ta funkcja jest przeciążonym otoką [pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[ATLPath::Przestrzenie cudzysłowu](#quotespaces)|Ta funkcja jest przeciążonym otoką [pathquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[ATLPath::RelativePathTo](#relativepathto)|Ta funkcja jest przeciążonym otokiem [pathrelativepathto](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[ATLPath::Usuńargi](#removeargs)|Ta funkcja jest przeciążonym otoką [pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).|
|[ATLPath::RemoveBackslash](#removebackslash)|Ta funkcja jest przeciążonym otoką dla [pathremoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).|
|[ATLPath::Usuńblaki](#removeblanks)|Ta funkcja jest przeciążonym otokiem [pathremoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).|
|[ATLPath::UsuńExtension](#removeextension)|Ta funkcja jest przeciążonym otoką [pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Ta funkcja jest przeciążonym otoką [pathremovefileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).|
|[ATLPath::Zmień nazwęWyświetlanie](#renameextension)|Ta funkcja jest przeciążonym otoką [pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[ATLPath::SkipRoot](#skiproot)|Ta funkcja jest przeciążonym otokiem [pathskiproot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[ATLPath::StripPath](#strippath)|Ta funkcja jest przeciążonym otokiem [pathstrippath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[ATLPath::StripToRoot](#striptoroot)|Ta funkcja jest przeciążonym otokiem [pathstripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Ta funkcja jest przeciążonym otoką [pathunquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

## <a name="atlpathaddbackslash"></a><a name="addbackslash"></a>ATLPath::AddBackSlash

Ta funkcja jest przeciążonym otoką dla [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Składnia

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [pliku PathAddBackslash.](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)

## <a name="atlpathaddextension"></a><a name="addextension"></a>ATLPath::AddExtension

Ta funkcja jest przeciążonym otoką [pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Składnia

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathAddExtension aby](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) uzyskać szczegółowe informacje.

## <a name="atlpathappend"></a><a name="append"></a>ATLPath::Dołącz

Ta funkcja jest przeciążonym otoką [pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Składnia

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathAppend szczegóły.](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)

## <a name="atlpathbuildroot"></a><a name="buildroot"></a>ATLPath::BuildRoot

Ta funkcja jest przeciążonym otoką [pathbuildroot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Składnia

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathBuildRoot szczegóły.](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)

## <a name="atlpathcanonicalize"></a><a name="canonicalize"></a>ATLPath::Canonicalize

Ta funkcja jest przeciążonym otoką [pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Składnia

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) uzyskać szczegółowe informacje.

## <a name="atlpathcombine"></a><a name="combine"></a>ATLPath::Kombajn

Ta funkcja jest przeciążonym otoką [pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

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

Zobacz PathCombine szczegóły.

## <a name="atlpathcommonprefix"></a><a name="commonprefix"></a>ATLPath::CommonPrefix

Ta funkcja jest przeciążonym otokiem [pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

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

Szczegółowe informacje można znaleźć w [pliku PathCommonPrefix.](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)

## <a name="atlpathcompactpath"></a><a name="compactpath"></a>ATLPath::CompactPath

Ta funkcja jest przeciążonym otoką [pathcompactpath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

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

Zobacz [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) szczegóły.

## <a name="atlpathcompactpathex"></a><a name="compactpathex"></a>ATLPath::CompactPathEx

Ta funkcja jest przeciążonym otoką [pathcompactpathex](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

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

Zobacz [PathCompactPathEx,](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) aby uzyskać szczegółowe informacje.

## <a name="atlpathfileexists"></a><a name="fileexists"></a>ATLPath::FileExists

Ta funkcja jest przeciążonym otoką [pathfileexists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Składnia

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathFileExists uzyskać](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) szczegółowe informacje.

## <a name="atlpathfindextension"></a><a name="findextension"></a>ATLPath::FindExtension

Ta funkcja jest przeciążonym otoką [pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Składnia

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathFindExtension aby](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) uzyskać szczegółowe informacje.

## <a name="atlpathfindfilename"></a><a name="findfilename"></a>ATLPath::FindFileName

Ta funkcja jest przeciążonym otoką [pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Składnia

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [pliku PathFindFileName.](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)

## <a name="atlpathgetdrivenumber"></a><a name="getdrivenumber"></a>ATLPath::GetDriveNumber

Ta funkcja jest przeciążonym otoką dla [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Składnia

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathGetDriveNumber, aby](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) uzyskać szczegółowe informacje.

## <a name="atlpathisdirectory"></a><a name="isdirectory"></a>ATLPath::IsDirectory

Ta funkcja jest przeciążonym otoką [pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w utorujeń pathisdirectory.

## <a name="atlpathisfilespec"></a><a name="isfilespec"></a>ATLPath::IsFileSpec

Ta funkcja jest przeciążonym otoką [pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [pliku PathIsFileSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)

## <a name="atlpathisprefix"></a><a name="isprefix"></a>ATLPath::IsPrefix

Ta funkcja jest przeciążonym otokiem [pathisprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsPrefix, aby](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) uzyskać szczegółowe informacje.

## <a name="atlpathisrelative"></a><a name="isrelative"></a>ATLPath::IsRelative

Ta funkcja jest przeciążonym otokiem [pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Składnia

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) aby uzyskać szczegółowe informacje.

## <a name="atlpathisroot"></a><a name="isroot"></a>ATLPath::IsRoot

Ta funkcja jest przeciążonym otoką [pathisroot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsRoot aby](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) uzyskać szczegółowe informacje.

## <a name="atlpathissameroot"></a><a name="issameroot"></a>ATLPath::IsSameRoot

Ta funkcja jest przeciążonym otoką [pathisSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathIsSameRoot aby](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) uzyskać szczegółowe informacje.

## <a name="atlpathisunc"></a><a name="isunc"></a>ATLPath::IsUNC

Ta funkcja jest przeciążonym otoką [pathisUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [pliku PathIsUNC.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)

## <a name="atlpathisuncserver"></a><a name="isuncserver"></a>ATLPath::Serwer ISUNCServer

Ta funkcja jest przeciążonym otoką [pathisUncserver](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [pliku PathIsUNCServer.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)

## <a name="atlpathisuncservershare"></a><a name="isuncservershare"></a>ATLPath::IsUNCServerShare

Ta funkcja jest przeciążonym otoką [pathisUncservershare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Składnia

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [dziele PathIsUNCServerShare.](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)

## <a name="atlpathmakepretty"></a><a name="makepretty"></a>ATLPath::MakePretty

Ta funkcja jest przeciążonym otokiem [pathmakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Składnia

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) szczegóły.

## <a name="atlpathmatchspec"></a><a name="matchspec"></a>ATLPath::MatchSpec

Ta funkcja jest przeciążonym otoką [pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Składnia

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [for pathmatchspec.](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)

## <a name="atlpathquotespaces"></a><a name="quotespaces"></a>ATLPath::Przestrzenie cudzysłowu

Ta funkcja jest przeciążonym otoką [pathquotespaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Składnia

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathQuoteSpaces,](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) aby uzyskać szczegółowe informacje.

## <a name="atlpathrelativepathto"></a><a name="relativepathto"></a>ATLPath::RelativePathTo

Ta funkcja jest przeciążonym otokiem [pathrelativepathto](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

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

Zobacz [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) aby uzyskać szczegółowe informacje.

## <a name="atlpathremoveargs"></a><a name="removeargs"></a>ATLPath::Usuńargi

Ta funkcja jest przeciążonym otoką [pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

### <a name="syntax"></a>Składnia

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [pliku PathRemoveArgs.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)

## <a name="atlpathremovebackslash"></a><a name="removebackslash"></a>ATLPath::RemoveBackslash

Ta funkcja jest przeciążonym otoką dla [pathremoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

### <a name="syntax"></a>Składnia

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRemoveBackslash szczegóły.](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)

## <a name="atlpathremoveblanks"></a><a name="removeblanks"></a>ATLPath::Usuńblaki

Ta funkcja jest przeciążonym otokiem [pathremoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

### <a name="syntax"></a>Składnia

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [pliku PathRemoveBlanks.](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)

## <a name="atlpathremoveextension"></a><a name="removeextension"></a>ATLPath::UsuńExtension

Ta funkcja jest przeciążonym otoką [pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

### <a name="syntax"></a>Składnia

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRemoveExtension aby](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) uzyskać szczegółowe informacje.

## <a name="atlpathremovefilespec"></a><a name="removefilespec"></a>ATLPath::RemoveFileSpec

Ta funkcja jest przeciążonym otoką [pathremovefileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

### <a name="syntax"></a>Składnia

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w pliku [PathRemoveFileSpec.](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)

## <a name="atlpathrenameextension"></a><a name="renameextension"></a>ATLPath::Zmień nazwęWyświetlanie

Ta funkcja jest przeciążonym otoką [pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Składnia

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathRenameExtension aby](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) uzyskać szczegółowe informacje.

## <a name="atlpathskiproot"></a><a name="skiproot"></a>ATLPath::SkipRoot

Ta funkcja jest przeciążonym otokiem [pathskiproot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Składnia

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) szczegóły.

## <a name="atlpathstrippath"></a><a name="strippath"></a>ATLPath::StripPath

Ta funkcja jest przeciążonym otokiem [pathstrippath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Składnia

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Szczegółowe informacje można znaleźć w [ścieżce PathStripPath.](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)

## <a name="atlpathstriptoroot"></a><a name="striptoroot"></a>ATLPath::StripToRoot

Ta funkcja jest przeciążonym otokiem [pathstripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Składnia

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathStripToRoot aby](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) uzyskać szczegółowe informacje.

## <a name="atlpathunquotespaces"></a><a name="unquotespaces"></a>ATLPath::UnquoteSpaces

Ta funkcja jest przeciążonym otoką [pathunquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Składnia

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Uwagi

Zobacz [PathUnquoteSpaces,](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) aby uzyskać szczegółowe informacje.
