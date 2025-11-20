# AGENTS.md

## Project Overview

BeOps is a comprehensive documentation site covering DevOps best practices, Kubernetes, and Site Reliability Engineering (SRE) principles. The project includes:

- **Jekyll-based documentation site** with GitHub Pages hosting
- **Python content generation tools** in `posts-generator/` directory
- **AI-powered content creation** using OpenAI and Google Gemini APIs

## Setup Commands

### Jekyll Site Setup
```bash
# Install Ruby dependencies
bundle install

# Start local development server
bundle exec jekyll serve --livereload

# Build for production
bundle exec jekyll build
```

### Python Tools Setup
```bash
# Navigate to posts-generator directory
cd posts-generator

# Create virtual environment
python -m venv py-feedparser

# Activate virtual environment
source py-feedparser/bin/activate  # On macOS/Linux
# or
py-feedparser\Scripts\activate     # On Windows

# Install dependencies
pip install -r requirements.txt
```

## Code Style

### Python (posts-generator/)
- Follow PEP 8 style guidelines
- Use meaningful variable names
- Add docstrings for functions and classes
- Use type hints where appropriate
- Keep functions focused and single-purpose

### Jekyll/Markdown
- Use consistent front matter format
- Follow Jekyll naming conventions for posts
- Use descriptive file names with dates
- Maintain consistent heading hierarchy

## Testing Instructions

### Python Tools Testing
```bash
cd posts-generator
python py-feedparser.py --test
python title_generator.py --test
python youtube_processor.py --test
```

### Jekyll Site Testing
```bash
# Test build locally
bundle exec jekyll build

# Check for broken links
bundle exec jekyll build --verbose
```

## Content Generation Workflow

### AI Content Creation
1. **Configuration**: Use config files in `posts-generator/configs/`
2. **Prompts**: Store AI prompts in `posts-generator/prompts.json`
3. **Output**: Generated content goes to `posts-generator/produced_posts/`
4. **Logging**: Check `posts-generator/logs/` for execution logs

### Key Files
- `py-feedparser.py`: Main content generation script
- `title_generator.py`: AI-powered title generation
- `youtube_processor.py`: YouTube content processing
- `openai_worker_4o.py`: OpenAI API integration

## Security Considerations

- **API Keys**: Store in `.env` file (not in version control)
- **Service Accounts**: Use `configs/service-account.json` for Google APIs
- **Configurations**: Keep sensitive configs out of public repos

## File Structure Guidelines

### Posts
- Store in `_posts/` with format: `YYYY-MM-DD-title.md`
- Use consistent front matter
- Include proper categories and tags

### Assets
- Images go in `assets/`
- Keep file sizes optimized
- Use descriptive filenames

## Deployment

### GitHub Pages
- Site automatically builds on push to main branch
- Check GitHub Actions for build status
- Live site: https://neverthesame.github.io/BeOps/

### Content Updates
1. Generate new content using Python tools
2. Review and edit generated content
3. Add to `_posts/` directory
4. Commit and push to trigger rebuild

### Agent Workflow Preferences
- When the user requests creation of a new post, automatically add the newly created Markdown file to git and push the commit to the `gh-pages` branch.

## Common Tasks

### Adding New Content
```bash
cd posts-generator
python py-feedparser.py --config config-4o.json
```

### Updating Dependencies
```bash
# Python
pip freeze > requirements.txt

# Ruby
bundle update
```

### Troubleshooting
- Check logs in `posts-generator/logs/`
- Verify API configurations
- Ensure virtual environment is activated
- Check Jekyll build output for errors

## AI Integration Notes

- **OpenAI**: Use GPT-4o for content generation
- **Google Gemini**: Use for YouTube content processing
- **Prompt Management**: All prompts stored in `prompts.json`
- **Rate Limiting**: Implement proper delays between API calls
- **Error Handling**: Log all API interactions for debugging
