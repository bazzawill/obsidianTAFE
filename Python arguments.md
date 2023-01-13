```python
import argparse

parser=argparse.ArgumentParser(
        description = "Testing argument parsing",
        epilog = 'written by bazzawill'
        )
parser.add_argument(
        '--url', '-u',
        help='url to test',
        metavar = 'python.org',
        default='python.org'
        )
parser.add_argument(
        '--search', '-s',
        help='search to test',
        metavar='cool',
        default='cool'
        )
parser.add_argument(
        '--selement', '-e',
        help='Element to find in the page for search box',
        metavar='q',
        default='q'
        )
args = parser.parse_args()
print(f'URL: {args.url}  Search: {args.search} Element: {args.selement}')

```