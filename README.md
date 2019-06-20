# dssp-notes
Guide to installing dssp on Mac
(Reference: https://github.com/cmbi/xssp)

[1] Install homebrew and required libraries:
  - Command-line tools for Xcode: `xcode-select --install`
  - Homebrew: `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
  - Boost: `brew install boost`
  - Automake: `brew install automake`

[2] Download and uncompress the xssp [source code archive](https://github.com/cmbi/xssp/releases) (version >= 2.2.6):
```bash
wget https://github.com/cmbi/xssp/archive/xssp-?.?.?.tar.gz
tar -zxvf xssp-?.?.?.tar.gz
cd xssp-?.?.?
```

[3] Configure and build the dssp executable:
```bash
./autogen.sh
./configure
make mkdssp
```

[4] Add mkdssp to path in `~/.bash_profile`:
```bash
export PATH="/path/to/xssp-?.?.?:$PATH"
```

[5] Done! Executable in terminal: `mkdssp` or Python:
```python
from Bio.PDB import DSSP, PDBParser
parser = PDBParser()
structure = parser.get_structure(<pdb_name>, <pdb_path>)
model = structure[0]
dssp = DSSP(structure[0], <pdb_path>, dssp='mkdssp')
```
