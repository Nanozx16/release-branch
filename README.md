# release-branch
- run: yarn lint
       - name: Validate RC changelog
         if: ${{ startsWith(github.head_ref, 'release/') }}
         run: yarn auto-changelog validate --rc
         run: yarn auto-changelog validate --rc --prettier
       - name: Validate changelog
         if: ${{ !startsWith(github.head_ref, 'release/') }}
         run: yarn auto-changelog validate
         run: yarn auto-changelog validate --prettier
       - name: Require clean working directory
         shell: bash
         run: |
