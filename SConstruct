import re
import os

sourcename = re.compile('^\d+[.]\d+[-]*')

env = Environment(tools = ['default', 'textfile'])

bld = Builder(action = 'asciidoc -d book -o $TARGET $SOURCE',
              suffix = '.html',
	      src_suffix = '.txt')

env.Append(BUILDERS = {'Asciidoc' : bld})

env.Textfile(
    target = '4Ps',  # concatenate files with a marker between
    source = sorted(File(x) for x in os.listdir('.') if sourcename.match(x))
    #[File('JH00_Remote_Pairing'), File('JH01_Kata_Pairs')]
)

env.Asciidoc('4Ps')


