## About

This repository contains my personal notes from various technical conferences, talks, and workshops.

## Conferences

| Conference | Date | Location | Topics | Notes |
|------------|------|----------|--------|-------|
| ARCtic | February 2026 | Oulu, Finland | iOS, Swift | [View Notes](./ConferenceNotes.docc/2026-ARCtic) |

## How to Use These Notes

### Viewing Online
Browse the rendered documentation on [GitHub Pages](https://oliver-binns.github.io/conference-notes/).

### Viewing on GitHub
The notes are organized in `.docc` folders, which you can browse directly on GitHub by clicking through the folders above.

### Viewing in Xcode
For the best reading experience with full DocC features:
1. Clone this repository
2. Open the `.docc` folder in Xcode 13 or later
3. Navigate through the documentation using Xcode's documentation viewer

### Viewing as Documentation
You can build and preview the documentation locally:
```bash
# Build the documentation
xcrun docc convert ConferenceNotes.docc \
  --fallback-display-name "Conference Notes" \
  --fallback-bundle-identifier com.oliver-binns.conference-notes \
  --output-path docs

# Preview in Xcode's documentation viewer
open -a Xcode ConferenceNotes.docc
```

## Contributing

Found a typo or want to add additional context? Contributions are welcome!

1. Fork this repository
2. Create a feature branch (`git checkout -b fix/typo-correction`)
3. Commit your changes (`git commit -m 'Fix typo in Arctic26 notes'`)
4. Push to the branch (`git push origin fix/typo-correction`)
5. Open a Pull Request

Please maintain the existing format and style when contributing.

## About Me

I'm a Lead Mobile Developer at Deloitte Digital with a passion for iOS development and the Swift community.
I attend conferences to stay current with the latest developments in mobile technology and share knowledge with fellow developers.

Connect with me:
- GitHub: [@Oliver-Binns](https://github.com/Oliver-Binns)
- LinkedIn: [Oliver Binns](https://www.linkedin.com/in/obinns)

## License

This repository is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details.

Feel free to use these notes for your own learning and reference.
If you find them helpful, consider giving this repository a star ⭐️ or sharing it with others in the community!
