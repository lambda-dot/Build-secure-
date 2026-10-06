# Deployment & Limitations

## Production Requirements
- HTTPS/TLS
- Secure environment variables
- Database configuration
- Monitoring and logging
- Backups
- Shared/distributed rate limiting for multi-instance scale
- Protected deployment environments

## Known Limitations

1. Payment is simulated.
2. Rate limiting is process-local.
3. The mock store is for supported local exploration and is not production shared persistence.
4. No full independent penetration test has been performed.
5. A full production security audit remains recommended.

Confidential credentials and deployment secrets are intentionally excluded from this public repository.
