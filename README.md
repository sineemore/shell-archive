# shell-archive

shell-archive is small, hackable shell script that creates installers simular to makeself.sh


The following command will tar ./dist folder and create installer.sh with custom header:

	$ shell-archive ./dist < header.sh > installer.sh


Example header.sh:

	set -e

	EXTRACT_DIR="$(mktemp -d)"
	printf 'Extracting to %s\n' "$EXTRACT_DIR" >&2

	after_extracting() {
		
		cd dist
		
		printf 'Installing...\n' >&2
		./bootstrap.sh
		
		printf 'Done\n' >&2
	}
